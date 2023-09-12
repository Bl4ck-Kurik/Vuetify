<template>
    <div id="app-content">
      <h1>{{ title }}</h1>
      <VuetifySidebar :items="sidebar"/>
      <div id="router-view">
        <router-view/>
      </div>
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
html {
  overflow-y: auto !important;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0c0c0c;
  max-width: 1700px;
  margin: auto;
}
#app-content {
  margin-top: 70px;
}
.v-application__wrap {
  min-height: 0 !important;
}
::-webkit-scrollbar {
  width: 5px;
}
::-webkit-scrollbar-track {
  display: none;
}
::-webkit-scrollbar-thumb {
  background: rgba(0, 0, 0, 0.5);
  border-radius: 5px 0 0 5px;
}
</style>