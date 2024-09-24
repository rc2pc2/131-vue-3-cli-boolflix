<script>
import { store } from '../store.js'

export default {
    data() {
        return {
            store,   
            userInput: '',
        }
    },
    methods:{
        // prendo la stringa che mi viene data come argomento
        sendNewQuery(){
            // e la stampo in console
            // console.log(message);

            // emettere un evento chiamato "searched" al parent
            this.$emit("searched");
            // this.store.searchedInput = message;
        }
    }
}
</script>

<template>
    <h2>
        HeaderSearch
    </h2>
    <div>
        <input type="text" v-model="store.searchedInput">
        <button @click="sendNewQuery">Search</button>
    </div>
</template>

<style scoped>
</style>