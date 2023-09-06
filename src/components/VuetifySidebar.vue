<template>
    <div>
        <v-layout style="z-index: 1005; position: sticky;">
            <v-navigation-drawer expand-on-hover rail>
                <v-list>
                    <v-list-item
                        :prepend-avatar='this.items.head[0].avatar'
                        :title='this.items.head[0].title'
                        :subtitle='this.items.head[0].subTitle'
                    ></v-list-item>
                </v-list>
                <v-divider></v-divider>
                <v-list density="compact" nav>
                    <v-list-item v-for="(item, index) in items.navList" :key="index" :value="index" @click="gotoLink(item.link)" :prepend-icon="item.icon" :title="item.label"></v-list-item>
                </v-list>
            </v-navigation-drawer>
        </v-layout>
    </div>
</template>
<script>
export default {
    props: {
        items: {
            type: Object,
            required: true,
        }
    }, 
    methods: {
        gotoLink(link) {
            window.location.href = link
        },    
    },
}
</script>
<style>
    
</style>