<template>
  <v-card>
    <v-container fluid>
      <v-layout wrap>
        <v-flex>
          <v-card-title>{{character.name}}</v-card-title>
        </v-flex>
      </v-layout>
    </v-container>
  </v-card>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data: () => ({}),
  props: ["character"]
});
</script>


<style lang="sass">

</style>
