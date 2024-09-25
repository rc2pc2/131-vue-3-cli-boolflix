<script>
import MainProductList from "./MainProductList.vue";
import { store } from '../store.js'

export default {
    data() {
        return {
            store
        }
    },
    components:{
        MainProductList
    }
}
</script>

<template>
    <Transition name="slide-fade">
        <MainProductList v-if="store.moviesList.length > 0" sectionTitle="Movies" :productsList="store.moviesList"/>
    </Transition>

    <Transition>
        <MainProductList v-if="store.tvSeriesList.length > 0" sectionTitle="TV Series" :productsList="store.tvSeriesList"/>
    </Transition>
</template>

<style scoped>
   /*
  Le animazioni di entrata e uscita possono utilizzare
  durate e funzioni di tempistica diverse.
*/
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>