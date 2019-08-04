<template>
  <div>
    <v-card class="mx-auto" max-width="400" flat>
      <v-container fluid grid-list-xl>
        <v-layout wrap>
          <v-flex>
            <v-toolbar>
              <v-btn
                depressed
                text
                @click="showDetails = !showDetails"
                :color="showDetails ? 'pink' : 'blue'"
              >{{showDetails ? "Hide Details": "Show Details"}}</v-btn>
            </v-toolbar>
          </v-flex>
          <v-flex v-for="character in characters" :key="character.id">
            <v-hover v-slot:default="{ hover }">
              <v-card @click="selectCharacter(character.id)" :elevation="hover ? 12: 0">
                <!-- <v-card v-if="characterSelected" :elevation="hover ? 18: 12"></v-card> -->
                <v-img
                  :src="character.img"
                  class="white--text"
                  height="200px"
                  gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                >
                  <v-card-title
                    class="fill-height align-end font-weight-light display-1"
                    v-text="character.name"
                  ></v-card-title>
                </v-img>
                <v-expand-transition>
                  <v-card-text transition="slide-y-transition" v-show="showDetails">
                    <div class="caption">
                      <b>Born:</b>
                      {{character.birth_year}}
                      <br />
                      <b>Height:</b>
                      {{character.height}}
                      <br />
                      <b>Mass:</b>
                      {{character.mass}}
                      <br />
                      <b>Force Power:</b>
                      {{character.force}}
                    </div>
                  </v-card-text>
                </v-expand-transition>
              </v-card>
            </v-hover>
            <v-expand-transition>
              <Character v-if="characterSelected" :character="selectedCharacter" />
            </v-expand-transition>
          </v-flex>
        </v-layout>
      </v-container>
    </v-card>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import charactersData from "@/assets/characters.json";
import Character from "@/components/characters/Character.vue";
export default Vue.extend({
  data: () => ({
    characters: charactersData,
    selectedCharacter: [],
    characterSelected: false,
    showDetails: true
  }),
  components: {
    Character
  },
  methods: {
    selectCharacter: function(id: string) {
      this.selectedCharacter = this.characters.filter(character => {
        // console.log(id, " this is the id");
        // console.log(character, `${character.name} is the current character`);
        // console.log(character.id === id, "returning");

        return character.id === id;
      })[0];
      console.log(this.selectedCharacter, "FOUND CHARACTER");
      this.characterSelected = !this.characterSelected;
    }
  }
});
</script>

<style lang="sass" scoped>

</style>
