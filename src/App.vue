<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Star</span>
        <span class="font-weight-light">Wars</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn to="/" text>Home</v-btn>
        <v-btn to="about" text>About</v-btn>
        <v-btn to="characters" text>Characters</v-btn>
      </v-toolbar-items>
    </v-app-bar>

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import router from "./router";

export default Vue.extend({
  name: "App",
  data: () => ({
    //
  }),
  methods: {
    route: (url: string, id?: string) => {
      if (id) {
        router.push({ path: url, params: { id: id } });
      } else {
        router.push(url);
      }
    }
  }
});
</script>

<style>
.link {
  color: black !important;
  text-decoration: none;
}
</style>


