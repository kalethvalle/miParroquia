<template>
  <v-app>
    <v-app-bar
      app
      color="secundary"
      dark
    >
      <div class="d-flex align-center">
        <h1>Mi Parroquia</h1>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="#"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-container fluid fill-height class="mt-0 pa-0">
      <router-view />
    </v-container>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    //
  }),
};
</script>
