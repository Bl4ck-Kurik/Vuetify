<template>
    <div class="create-card">
        <FormKit
            type="form"
            id="create-card"
            @change="submitToParent"
            @keydown.enter.prevent
            :actions="false"
         >
            <FormKit type="text" id="card-title" label="Title"/>
            <FormKit type="textarea" id="card-content" label="Content" rows="10"/>
        </FormKit>
    </div>
</template>
<script>
export default {
    methods: {
        submitToParent(event) {
            const id = event.target.id
            const value = event.target.value
            this.$emit('updateValue', { id, value})
        }
    },
}
</script>
<style>
    #create-card {
        width: 400px;
    }
</style>