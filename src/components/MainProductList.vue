<script>
import MainProductItem from "./MainProductListItem.vue"

export default {
    props:{
        productsList: {
            type: Array,
            required : true, 
        },
        sectionTitle:{
            type: String,
            required: true,
        }
    },
    data() {
        return {
        }
    },
    components:{
        MainProductItem
    }
}
</script>

<template>
    <h2>
        {{ sectionTitle }}
    </h2>
    <TransitionGroup name="list" tag="ul">
        <MainProductItem v-for="product in productsList" :key="product.id" :product="product"/>
    </TransitionGroup>
</template>

<style scoped>
.list-move, /* applica la transizione agli elementi in movimento */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

/* assicurati che gli elementi in uscita siano esclusi dal flusso del layout in modo 
   che le animazioni in movimento possano essere calcolate correttamente.  */
.list-leave-active {
  position: absolute;
}
</style>