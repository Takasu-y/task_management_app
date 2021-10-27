<template>
<!-- App.vue -->

<v-app>
  <!-- <v-navigation-drawer app> -->
    <!-- -->
  <!-- </v-navigation-drawer> -->

  <v-app-bar app>
    <h1>Task Management App</h1>
  </v-app-bar>

  <!-- アプリケーションのコンポーネントに基づいてコンテンツのサイズを決定 -->
  <v-main>

    <!-- アプリケーションに適切なgutterを提供 -->
    <v-container>
      <v-row class="mt-10"
      >
      <task-manager></task-manager>
      </v-row>



      <!-- vue-routerを使用する場合 -->
      <router-view></router-view>
    </v-container>
  </v-main>

  <v-footer app>
    <!-- -->
  </v-footer>
</v-app>
</template>

<script>
// import draggable from 'vuedraggable'
import taskManager from './components/taskManager.vue'

export default {
  name: 'App',

  components: {
    taskManager,
    // draggable,
  },

  data() {
      return {
        //
      }
  },
};
</script>
