<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import { store } from './store.js'
import axios from 'axios';

export default {
    data() {
      return {
        store,
        apiUrl : "https://api.themoviedb.org/3/search/",
        apiKey: "e99307154c6dfb0b4750f6603256716d",        
      }
    },
    components:{
      AppHeader,
      AppMain
    },
    methods:{
      // logInfo(){
      //   console.log("Evento arrivato in app.vue!");
      //   console.log(this.store.searchedInput);
      // },

      fetchMoviesAndSeries(newQuery){
        this.getMovies(newQuery);
        this.getTvSeries(newQuery);
      },

      getMovies(query){
        // console.log(query);
        axios.get(this.apiUrl + "movie", {
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
      },

      getTvSeries(query){
        // console.log(query);
        axios.get(this.apiUrl + "tv", {
            params: {
              api_key: this.apiKey,
              query: query
            }
          })
          .then((response) => {
            console.log(response.data.results);
            this.store.tvSeriesList = response.data.results;
          })
          .catch(function (error) {
            console.log(error);
          });
      },
      logger(){
        console.log('ciao');
      }
    },
  

}
</script>
<!-- impostiamo un evento custom in arrivo da HeaderSearch -->

<template>
  <AppHeader @new-search="fetchMoviesAndSeries(store.searchedInput)" />
  <AppMain />
</template>

<style lang="scss">
  // @use '../node_modules/flag-icons/sass/flag-icons.scss';
  @use './styles/general.scss';

</style>