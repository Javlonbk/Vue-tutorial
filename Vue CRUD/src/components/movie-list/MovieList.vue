<template>
    <ul class="movie-list list-group">
        <MovieListItem v-for="movie in movies" :movie="movie" :key="movie.id" @onToggle="$emit('onToggle', $event)" @onDelete="$emit('onDelete', $event)" />
        
    </ul>
</template>
<script>
import MovieListItem from '../movie-list-item/MovieListItem.vue';

export default {
    components:{
        MovieListItem
    },
    props:{
        movies:{
            type: Object,
            required: true
        }
        
    }
   
}
</script>
<style scoped>
   
</style>