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
      
  },
  created() {
    axios
      .get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
      .then(
        resp => {

          this.store.characters = resp.data.data.slice(0, 20);
            if (this.store.characters.length == 20) {
              this.store.apiLoaded = true;
            }
    });
  }
    
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