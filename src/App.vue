<template>
    <h1>{{ title }}</h1>
    <VuetifySidebar :items="sidebar"/>
    <div id="router-view">
      <router-view/>
    </div>
  </template>
  
  <script>
  import FlexNav from '@/components/FlexNav.vue'
  import VuetifyNav from '@/components/VuetifyNav.vue'
  import VuetifySidebar from '@/components/VuetifySidebar.vue'

  export default {
    name: 'App',
    data () {
      return {
        title: 'My First Vue APP',
        sidebar: {
          head: [
            {
              avatar: 'https://randomuser.me/api/portraits/lego/6.jpg',
              title: 'Juan Bricktez',
              subTitle: 'juan.bricktez@legomail.com'
            }
          ],
          navList: [
            {
              icon: 'mdi-home',
              label: 'Home',
              link: '/',
            },
            {
              icon: 'mdi-account',
              label: 'Your Account',
              link: '#account',
            },
            {
              icon: 'mdi-newspaper-variant-multiple',
              label: 'Latest News',
              link: '#news',
            },
            
          ] 
        }
      }
    },
    methods: {
      
    },
    components: {
      FlexNav,
      VuetifyNav,
      VuetifySidebar,
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
    margin: 60px 0 120px;
  }
  </style>