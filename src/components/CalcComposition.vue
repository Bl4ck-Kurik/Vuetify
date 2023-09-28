<template>
    <div>
        <table class="calculator">
            <tr>
                <v-card class="screen">
                    <h2 ref="screenH2">{{ prevInput + selectedOperator + currentInput }}</h2>
                </v-card>
            </tr>
            <tr>
                <v-btn @click="pressed('1')">1</v-btn>
                <v-btn @click="pressed('2')">2</v-btn>
                <v-btn @click="pressed('3')">3</v-btn>
                <v-btn @click="pressed('+')">+</v-btn>
            </tr>
            <tr>
                <v-btn @click="pressed('4')">4</v-btn>
                <v-btn @click="pressed('5')">5</v-btn>
                <v-btn @click="pressed('6')">6</v-btn>
                <v-btn @click="pressed('-')">-</v-btn>
            </tr>
            <tr>
                <v-btn @click="pressed('7')">7</v-btn>
                <v-btn @click="pressed('8')">8</v-btn>
                <v-btn @click="pressed('9')">9</v-btn>
                <v-btn @click="pressed('*')">*</v-btn>
            </tr>
            <tr>
                <v-btn @click="pressed('c')">C</v-btn>
                <v-btn @click="pressed('0')">0</v-btn>
                <v-btn @click="pressed('=')">=</v-btn>
                <v-btn @click="pressed('/')">/</v-btn>
            </tr>
        </table>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, watch, nextTick} from 'vue'

let prevInput = ref('')
let currentInput = ref('')
const numbers = ['1', '2', '3', '4', '5', '6', '7', '8', '9', '0']
const operators = ['+', '-', '*', '/']
let selectedOperator = ref('')
const screenH2 = ref(null)

const pressed = (value) => {
    if (value === '=' || value === 'Enter') calculate()
    else if (value === 'c') {
        prevInput.value = ''
        currentInput.value = ''
        selectedOperator.value = ''
    } else if (numbers.includes(value)) {
        currentInput.value = currentInput.value + value
    } else if (operators.includes(value)) {
        calculate()
        prevInput.value = currentInput.value
        currentInput.value = ''
        selectedOperator.value = value
    }
}
const calculate = () => {
    if (selectedOperator.value === '+') {
        currentInput.value = +prevInput.value + +currentInput.value
    } else if (selectedOperator.value === '-') {
        currentInput.value = prevInput.value - currentInput.value
    } else if (selectedOperator.value === '*') {
        currentInput.value = prevInput.value * currentInput.value
    } else if (selectedOperator.value === '/') {
        currentInput.value = prevInput.value / currentInput.value
    }
    prevInput.value = ''
    selectedOperator.value = ''
}
const handleKey = (e) => pressed(e.key)
const scrollX = () => {
    if (screenH2.value) {
        screenH2.value.scrollLeft = screenH2.value.scrollWidth
    }
}

onMounted(() => window.addEventListener('keydown', handleKey))
onUnmounted(() => window.removeEventListener('keydown', handleKey))

watch(
    currentInput,
    async () => {
        await nextTick()
        scrollX()
    }
)
</script>

<style scoped>
.calculator {
    margin: auto;
    max-width: 260px;
}
.screen {
    height: 38px;
    margin-bottom: 15px;
    max-width: 256px;
}
.screen h2 {
    overflow-wrap: normal;
    overflow-x: scroll;
    overflow-y: hidden;
}
</style>