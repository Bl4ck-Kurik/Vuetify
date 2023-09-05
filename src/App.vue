<template>
    <h1>{{ title }}</h1>
    <FlexNav :items="navItems" />
    <VuetifyNav :items="navItems"/>
    <div id="router-view">
      <router-view/>
    </div>
  </template>
  
  <script>
  import FlexNav from '@/components/FlexNav.vue'
  import VuetifyNav from '@/components/VuetifyNav.vue'

  export default {
    name: 'App',
    data () {
      return {
        title: 'My First Vue APP',
        navItems: [
          {
            label: "Home",
            link: "#1",
          },
          {
            label: "Example Tab",
            link: "#2",
            subItems: [
              {
                label: "sub 1",
                link: "#sub1",
              },
              {
                label: "sub 2",
                link: "#sub2",
              },
            ],
          },
          {
            label: "Example Tab",
            link: "#2",
            subItems: [
              {
                label: "sub 1",
                link: "#sub1",
              },
              {
                label: "sub 2",
                link: "#sub2",
              },
            ],
          },
        ],
      }
    },
    methods: {
      
    },
    components: {
      FlexNav,
      VuetifyNav,
    }
  }
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #0c0c0c;
    /* background-color: #000; */
    margin: 60px 0 120px;
  }
  </style>