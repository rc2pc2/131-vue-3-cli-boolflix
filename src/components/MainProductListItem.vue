<script>
export default {
    data() {
        return {
            // imageUrl: "https://image.tmdb.org/t/p/w780/"
        }
    },
    props:{
        product: {
            required: true,
            type: Object
        }
    },
    computed:{
        newOriginalLanguage(){
            if (this.product.original_language === "en"){
                return "gb";
            } else if ( this.product.original_language === "ja" ){
                return "jp";
            } else if ( this.product.original_language === "ko" ){
                return "kr";
            } else {
                return this.product.original_language;
            }
        },
        title(){
            if (this.product.title){
                return this.product.title;
            } else {
                return this.product.name;
            }
        },
        originalTitle(){
            if (this.product.original_title){
                return this.product.original_title;
            } else {
                return this.product.original_name;
            }
        },
        vote(){
            return Math.round(this.product.vote_average / 2);
        },
        imageUrl(){
            if (this.product.poster_path !== null && this.product.poster_path !== undefined ){
                return `https://image.tmdb.org/t/p/w780/${this.product.poster_path}`;
            } else {
                return `https://ih1.redbubble.net/image.3572931424.7035/fposter,small,wall_texture,product,750x1000.jpg`;
            }
        }
    }
}
</script>

<template>
    <li>
        <img :src="imageUrl" alt="">
        <p>
            {{ title }} == {{ originalTitle }} ==  <span :class="`fi fi-${newOriginalLanguage}`"></span> 
            == {{ product.vote_average }}
            === <span v-for="n in vote">*</span><span v-for="n in 5 - vote">#</span>
        </p>
    </li>
</template>

<style lang="scss" scoped>
img{
    height: 100px;
}
</style>