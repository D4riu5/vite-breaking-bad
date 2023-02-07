<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import { store } from "./store.js";

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
          store,
          // characters: '',
          // apiLoaded: false,
        }
    },
  methods:{
    getCharacters() {
      axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
          // params: {
          //     race: this.store.raceValue
          //   }
        })
        .then(
          resp => {

            this.store.characters = resp.data.data.slice(0, 20);
            this.store.apiLoaded = true;
      });
    },
    getArchetypes() {
      axios
        .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then(
          resp => {
            this.store.archetypes = resp.data
          }
        )
    }
  },
  created() {
    this.getCharacters();
    this.getArchetypes()
  },
    
};
</script>


<template>
  <AppHeader/>
  <!-- <AppMain :charactersList="characters" :charactersCount="characters.length"/> -->
  <AppMain/>
</template>


<style lang="scss">
@use "./styles/main";
</style>