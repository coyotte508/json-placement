<template>
  <v-app dark>
    <v-app-bar app dense :fixed="fixed">
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container fluid class="pb-0">
        <nuxt />
      </v-container>
    </v-main>
    <!-- <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      title: 'Boardgame Data Generator',
      fixed: false
    };
  }
};
</script>
