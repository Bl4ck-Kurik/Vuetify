<template>
    <div>
        <div class="v-nav">
            <v-btn ref="buttonsWithMenu" :append-icon="subIcon(item.subItems)" color="primary" v-for="(item, index) in items" :key="index" :value="index" @click="gotoLink(item.link)">
                {{ item.label }}
                <v-menu open-on-hover activator="parent" v-if="item.subItems && item.subItems.length > 0">
                    <v-list>
                        <v-list-item v-for="(subItem, index) in item.subItems" :key="index" :value="index">
                            <v-list-item-title @click="gotoLink(subItem.link)">
                                {{ subItem.label }}
                            </v-list-item-title>
                        </v-list-item>
                    </v-list>
                </v-menu>
            </v-btn>
        </div>
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
        subIcon(subContent) {
            if (subContent && subContent.length > 0) {
                return 'mdi-menu-right'
            }
            return
        }
    },
    mounted() {
        this.$nextTick(() => {
            const buttons = this.$refs.buttonsWithMenu
            buttons.forEach((vBtnComponent) => {
                const buttonElem = vBtnComponent.$el
                if (buttonElem && buttonElem.hasAttribute('aria-expanded')) {
                    const observer = new MutationObserver((mutationsList) => {
                        for(let mutation of mutationsList) {
                            if (mutation.attributeName === 'aria-expanded') {
                                const isExpanded = buttonElem.getAttribute('aria-expanded') === 'true'
                                if (isExpanded) {
                                    buttonElem.classList.add('menu-expanded')
                                } else {
                                    buttonElem.classList.remove('menu-expanded')
                                }
                            } else {
                            }
                        }
                    })
                    observer.observe(buttonElem, { attributes: true });
                }
            })
        })
    }
}
</script>
<style>
    .v-nav .v-btn {
        border-radius: 0;
        background-color: #1866c00e;
        box-shadow: none;
        /* box-shadow: 0px 3px 5px 0px var(--v-shadow-key-umbra-opacity, rgba(0, 0, 0, 0.2)), 0px 2px 2px 0px var(--v-shadow-key-penumbra-opacity, rgba(0, 0, 0, 0.14)), 0px 1px 5px 0px var(--v-shadow-key-penumbra-opacity, rgba(0, 0, 0, 0.12)); */
    }
    .v-nav .v-btn:first-child {
        border-radius: 0 0 0 4px;
    }
    .v-nav .v-btn:last-child {
        border-radius: 0 0 4px 0;
    }
    .v-nav .menu-expanded span.v-btn__append>i {
        transform: rotate(90deg);
    }
    .v-nav .v-btn span.v-btn__append>i {
        transition: transform 0.2s ease-in-out;
    }
</style>