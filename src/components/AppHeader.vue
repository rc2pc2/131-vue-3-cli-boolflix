<script>
import HeaderSearch from "./HeaderSearch.vue";

export default {
    data() {
        return {
        }
    },
    methods:{
        sendNewQuery(){
            this.$emit("newSearch");
        }
    },
    components:{
        HeaderSearch
    }
}
</script>

<template>
    <HeaderSearch @searched="sendNewQuery" />
</template>

<style scoped>
</style>