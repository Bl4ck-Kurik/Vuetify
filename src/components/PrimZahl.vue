<template>
    <div>
        <v-btn @click="currentPrime = ''">Clear</v-btn>
        <p>{{ currentPrime }}</p>
        <v-btn @click="prime" style="margin-top: 20px;">Start Prime</v-btn>
    </div>
</template>
<script>
export default {
    data() {
        return {
            maxNumber: 1000,
            currentPrime: ''
        }
    },
    methods: {
        prime() {
            this.currentPrime = ''
            const duration = 2000
            const startTime = Date.now()
            for (let i = 2; ; i++) {
                if (Date.now() - startTime > duration) {
                    break
                }
                let isPrime = true;
                let sr = Math.sqrt(i);
                for (let d = 2; d <= sr; d++) {
                    if (i % d == 0) {
                        isPrime = false
                        break
                    }
                }
                if (isPrime) {
                    this.currentPrime = this.currentPrime + i + '; '
                    // console.log(i)
                }
            }  
        }
    },
}
</script>
<style>
    
</style>