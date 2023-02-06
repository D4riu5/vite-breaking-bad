<script>

export default {
    name: 'AppMain',
    components: {

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
                            Found "some" cards
                        </div>
                        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-5 p-4">
                            <div v-for="i in 20" class="col text-center">
                                <div class="bg-primary p-3 my-2">
                                    <div>
                                        <img class="img-fluid" src="https://picsum.photos/200/300" alt="">
                                    </div>
                                    <div>
                                        <h5 class="py-3">
                                            Character name
                                        </h5>
                                        <h6>
                                            Char status
                                        </h6>
                                    </div>
                                </div>
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
