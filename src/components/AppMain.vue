<script>
import MainProductItem from "./MainProductItem.vue"
import { store } from '../store.js'

export default {
    data() {
        return {
            store
        }
    },
    components:{
        MainProductItem
    }
}
</script>

<template>
    <ul>
        <MainProductItem v-for="movie in store.moviesList" :key="movie.id" :movie="movie"/>
    </ul>
</template>

<style scoped>
</style>