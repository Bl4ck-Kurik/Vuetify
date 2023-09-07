<template>
    <div>
        <v-btn @click="openOverlay">Create Card</v-btn>
        <v-overlay v-model="create" >
            <div class="overlay-content" style="height: 100%; width: 100%;" @click.stop>
                <v-btn @click="closeOverlay">Close</v-btn>
                <Create/>
            </div>
        </v-overlay>
    </div>
</template>
<script>
import Create from '@/components/CreateCard.vue'

export default {
    components: {
        Create,
    },
    data() {
        return {
            create: false,
        }
    },
    methods: {
        openOverlay() {
            this.create = true
        },
        closeOverlay() {
            this.create = false
        },
    },
}
</script>
<style>
    
</style>