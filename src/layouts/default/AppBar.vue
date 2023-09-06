<template>
  <v-app-bar flat>
    <v-app-bar-title>
      <Nav :items="navItems"/>
    </v-app-bar-title>
  </v-app-bar>
</template>

<script>
import Nav from '@/components/VuetifyNav.vue'

export default {
  data() {
    return {
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
        ],
    }
  },
  components: {
    Nav,
  }
}
</script>
<style>
.v-toolbar-title__placeholder .v-nav {
  margin: 6px 15px 20px 0;
}
.v-toolbar-title__placeholder .v-nav .v-btn {
  height: 50px;
}
.v-toolbar {
  background: linear-gradient(180deg, rgb(255, 255, 255) 80%, rgba(255,255,255,0.9472163865546218) 85%, rgba(255,255,255,0.8799894957983193) 90%, rgba(255,255,255,0.29735644257703087) 95%, rgba(255,255,255,0) 100%) !important;
}
</style>