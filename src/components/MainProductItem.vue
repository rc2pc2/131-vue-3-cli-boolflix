<script>
export default {
    data() {
        return {
            
        }
    },
    props:{
        movie: {
            required: true,
            type: Object
        }
    }
}
</script>

<template>
    <li>
        <p>
            {{ movie.title }}
        </p>
        <p>
            {{ movie.original_title }}
        </p>
        <p>
            {{ movie.original_language }}
        </p>
        <p>
            {{ movie.vote_average }}
        </p>
    </li>
</template>

<style scoped>
</style>