<script>
import CharacterCard from './AppMain/CharacterCard.vue';
import { store } from "../store.js";
import axios from 'axios';

export default {
    name: 'AppMain',
    components: {
        CharacterCard,
        store,
    },
    // props: {
    //     charactersList: {
    //         type: Array,
    //         default: [],
    //     },
    //     charactersCount: {
    //         type: Number,
    //         default: 0,
    //     },
    // },
    data() {
        return {
            store,
        }
    },
    methods:{
    getCharacters() {

      let url = `https://db.ygoprodeck.com/api/v7/cardinfo.php`;
      this.store.archetype ? url += `?archetype=${this.store.archetype}` : url;

      axios
        .get(url)
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
}
</script>


<template>
    <main class="bg-primary">
        <div class="container">
            <div class="row">
                <div class="col-10 offset-1">
                    <div class="row py-4">
                        <div class="col-3">
                            <select @change="getCharacters()" v-model="store.archetype" class="form-select" aria-label="Default select example">
                                <option value="" selected>Select Archetype</option>
                                <option v-for="archetype in store.archetypes" :value="archetype.archetype_name">{{ archetype.archetype_name}}</option>
                            </select>
                        </div>
                    </div>
                    <div v-if="store.apiLoaded" class="p-4 bg-secondary mb-5">
                        <div class="bg-dark text-white p-2">
                            Found {{ store.characters.length }} cards
                        </div>
                        <div  class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5 p-4">
                            <!-- <div v-for="character in store.characters" class="col text-center">
                                <CharacterCard :character="character"/>
                            </div> -->

                            <CharacterCard/>
                            
                        </div>   
                    </div>
                    <div v-else class="py-5 d-flex justify-content-center">
                        <span class="loader"></span>
                    </div> 
                </div>
            </div>
        </div>    
    </main>
</template>


<style lang="scss" scoped>
main{
    min-height: 100vh;

    img{
        width: 100%;
        aspect-ratio: 1.4/2;
    }


    // Spinner
    .loader {
        width: 88px;
        height: 88px;
        border: 5px solid #FFF;
        border-bottom-color: transparent;
        border-radius: 50%;
        display: inline-block;
        box-sizing: border-box;
        animation: rotation 1s linear infinite;
    }

    @keyframes rotation {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    } 

}
</style>
