<template>
  <div class="app">
    <div class="content">
      <AppInfo :allMovies="movies.length" />
      <div class="searchPanel">
        <SearchPanel @onUpdate="onUpdateHandler"  />
        <AppFilter @onFilter="onUpdateFilterHandler" />
      </div> 
      <MovieList 
      :movies="onFilterHandler(onSearchHandler(movies, term), filter)" 
      @onToggle="onToggleHandler"
      @onDelete="onDeleteHandler"
      />
      <AddForm @createMovie="createMovie" />
    </div>
  </div>
</template>

<script>
import AppInfo from '@/components/app-info/AppInfo.vue';
import SearchPanel from './components/search-panel/SearchPanel.vue'
import AppFilter from './components/app-filter/AppFilter.vue';
import AddForm from './components/add-form/AddForm.vue';
import MovieList from './components/movie-list/MovieList.vue'

export default{
components: {
  AppInfo,
  SearchPanel,
  AppFilter,
  AddForm,
  MovieList
},
data(){
        return{
            movies:[
            {
                id:1,
                name:'Iron Man',
                view:2000,
                like:true,
                favorite:false
            },
            {
                id:2,
                name:'Avengers',
                view:3000,
                like:false,
                favorite:true
            },
            {
                id:3,
                name:'Thor',
                view:1000,
                like:false,
                favorite:false
            },

        ],
        term: '',
        filter: ''
        }
        
    },
    methods:{
      createMovie(movie){
        this.movies.push(movie)
      },
      onToggleHandler({id, prop}){
          this.movies.map(movie => {
            if(movie.id == id){
              movie[`${prop}`] = !movie[`${prop}`]
            }
          })
      },
      onDeleteHandler(id){
        this.movies = this.movies.filter(movie => {
          return movie.id !== id
        })
      },
      onSearchHandler(movies, term){
        if(!term.length) return movies
        else return movies.filter(movie => {
          return movie.name.toLowerCase().includes(term.toLowerCase()) // movie.name.toLowerCase().indexOf() > -1
        })
      },
      onUpdateFilterHandler(filter){
        this.filter = filter
      },
      onUpdateHandler(term){
        this.term = term
      },
      onFilterHandler(movies, filter){
        switch(filter){
          case 'favorite': return movies.filter(movie => movie.like); break;
          case 'mostView': return movies.filter(movie => movie.view >= 2000); break;
          default: return movies
        }
      }
      }
}
</script>

<style>
.app{
  height: 100vh;
  color: #000;
}
.content{
  width: 70%;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
  box-sizing: border-box;
}
</style>