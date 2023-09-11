<template>
    <div class="cards">
        <v-btn @click="openOverlay">Create Card</v-btn>
        <v-overlay class="card-create" v-model="create" style="padding: auto;">
                <div class="content-inner">
                    <Create/>
                    <div class="buttons">
                        <v-btn @click="closeOverlay">Close</v-btn>
                        <v-btn color="primary">Save</v-btn>
                    </div>
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
    .card-create .v-overlay__content {
        width: 100vw;
        height: 100vw;
    }
    .content-inner {
        display: grid;
        place-items: center;
        max-width: 800px;
        margin: 50px auto;
        padding: 30px;
        background-color: white;
        border-radius: 10px;
    }
    .buttons > * {
        margin: 0 5px;
    }
</style>