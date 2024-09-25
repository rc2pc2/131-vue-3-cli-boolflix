<script>
import { store } from '../store.js'

export default {
    data() {
        return {
            store,   
        }
    },
    methods:{
        sendNewQuery(){
            // attivo un evento chiamato "searched" al parent
            this.$emit("searched");
        }
    }
}
</script>

<template>
    <h2>
        HeaderSearch
    </h2>
    <div>
        <input type="text" v-model.trim="store.searchedInput" @keyup.enter="sendNewQuery">
        <button @click="sendNewQuery">Search series and movies</button>
    </div>
</template>

<style scoped>
</style>