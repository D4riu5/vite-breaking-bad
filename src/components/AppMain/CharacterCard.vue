<script>

export default {
    name: 'CharacterCard',
    components: {

    },
    props: {
        character: Object
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
    <div class="bg-primary p-3 my-2 my_card">
        <div>
            <img class="img-fluid" :src="character.card_images[0].image_url" alt="">
        </div>
        <div class="">
            <h5 class="py-3">
                {{character.name}}
            </h5>
            <h6>
                {{character.race}}
            </h6>
        </div>
    </div>
</template>


<style lang="scss" scoped>
.my_card{
    min-height: 390px;
}
</style>
