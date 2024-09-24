<script>
import HeaderSearch from "./components/HeaderSearch.vue";
import AppMain from "./components/AppMain.vue";
import { store } from './store.js'
import axios from 'axios';

export default {
    data() {
      return {
        store,
        apiUrl : "https://api.themoviedb.org/3/search/movie",
        apiKey: "e99307154c6dfb0b4750f6603256716d",        
      }
    },
    components:{
      HeaderSearch,
      AppMain
    },
    methods:{
      // logInfo(){
      //   console.log("Evento arrivato in app.vue!");
      //   console.log(this.store.searchedInput);
      // },

      getMovies(query){
        console.log(query);
        axios.get(this.apiUrl, {
            params: {
              api_key: this.apiKey,
              query: query
            }
          })
          .then((response) => {
            console.log(response.data.results);
            this.store.moviesList = response.data.results;
          })
          .catch(function (error) {
            console.log(error);
          });
      }
    }
}
</script>
<!-- impostiamo un evento custom in arrivo da HeaderSearch -->

<template>
  <HeaderSearch @searched="getMovies(store.searchedInput)" />
  <AppMain />
</template>

<style lang="scss">
  @use './styles/general.scss';


</style>