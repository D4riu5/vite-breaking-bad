<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },
  data() {
        return {
          characters: '',
          apiLoaded: false,
        }
    },
  methods:{
      
  },
  created() {
    axios
      .get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
      .then(
        resp => {

          this.characters = resp.data.data.slice(0, 20);
            if (this.characters.length == 20) {
              this.apiLoaded = true;
            }
    });
  }
    
};
</script>


<template>
  <AppHeader/>
  <AppMain :charactersList="characters" :charactersCount="characters.length"/>
</template>


<style lang="scss">
@use "./styles/main";
</style>