<script>
import { store } from "../store.js";

export default {
    name: 'AppHeader',
    components: {
        store,
    },
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
    <header class="text-white p-4 bg-secondary">

        <h2>Yu-Gi-Oh Api</h2>

    </header>
</template>


<style lang="scss" scoped>
</style>
 