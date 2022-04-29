<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6"> Vue.js </v-list-item-title>
          <v-list-item-subtitle> Lista de tarefas </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>
      

    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Laboratorio</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <HomeComponet />
    </v-main>
  </v-app>
</template>

<script>
  import HomeComponet from '../components/home/Home.vue'
  export default {
    data: () => ({ drawer: null }),
    components:{
      HomeComponet
    }
  }
</script>