<script>
import { store } from "../../store.js";

export default {
    name: 'CharacterCard',
    components: {
        store,
    },
    // props: {
    //     character: Object
    // },
    data() {
        return {
            store,
        }
    },
    methods:{
        
    },
}
</script>


<template>
    <!-- <div class="bg-primary p-3 my-2 my_card">
        <div>
            <img class="img-fluid" :src="character.card_images[0].image_url" alt="">
        </div>
        <div class="text-white">
            <h5 class="py-3">
                {{character.name}}
            </h5>
            <h6>
                {{character.race}}
            </h6>
        </div>
    </div> -->

    <div v-for="character in store.characters" class="col text-center">
        <div class="bg-primary p-3 my-3 my_card">
            <div>
                <img class="img-fluid" :src="character.card_images[0].image_url" alt="">
            </div>
            <div class="sub-card d-flex flex-column justify-content-between text-white">
                <h5 class="py-3">
                    {{character.name}}
                </h5>
                <h6>
                    {{character.race}}
                </h6>
            </div>
        </div>
    </div>
    
</template>


<style lang="scss" scoped>
.my_card{
    // min-height: 390px;
    min-width: 150px;
    
    h5{
        font-size: 1.15rem!important;
    }

    .sub-card{
        min-height: 150px;
    }
}


</style>
