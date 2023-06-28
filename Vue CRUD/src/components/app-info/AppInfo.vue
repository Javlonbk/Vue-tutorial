<template>
    <div class="appInfo">
        <p class="fs-3 text-uppercase">All Movies: {{ allMovies }}</p>
        <p class="fs-3 text-uppercase">Watched movies: 0</p>
    </div>
</template>

<script>
export default{
    props:{
        allMovies:{
            type:Object,
            required:true
        }
    }
}
</script>

<style scoped>
.appInfo{
    padding: 1.5rem;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>