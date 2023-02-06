<script>
import CharacterCard from './AppMain/CharacterCard.vue';

export default {
    name: 'AppMain',
    components: {
        CharacterCard,
    },
    props: {
        charactersList: {
            type: Array,
            default: [],
        },
        charactersCount: {
            type: Number,
            default: 0,
        },
    },
    data() {
        return {
            
        }
    },
    methods:{
        
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
                            <select class="form-select" aria-label="Default select example">
                                <option disabled selected>Open this select menu</option>
                                <option value="1">One</option>
                                <option value="2">Two</option>
                                <option value="3">Three</option>
                            </select>
                        </div>
                    </div>
                    <div class="p-4 bg-secondary mb-5">
                        <div class="bg-dark text-white p-2">
                            Found {{ charactersCount }} cards
                        </div>
                        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-5 p-4">
                            <div v-for="character in charactersList" class="col text-center">
                                <CharacterCard :character="character"/>
                            </div>
                        </div>    
                    </div>
                </div>
            </div>
        </div>    
    </main>
</template>


<style lang="scss" scoped>
main{
    height: 100%;

    img{
        width: 100%;
        aspect-ratio: 1.4/2;
    }

}
</style>
