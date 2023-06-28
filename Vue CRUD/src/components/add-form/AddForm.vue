<template>
    <div class="add-form ">
         <h3>Add new movie</h3>
         <form class="d-flex" @submit.prevent>
            <input 
            type="text" 
            class="form-control new-movie-label" 
            placeholder="Movie name"
            :value="name"
            @input="name=$event.target.value"
            />
            
            <input 
            type="number" 
            class="form-control new-movie-label" 
            placeholder="Numbers of watched"
            :value="view"
            @input="view=$event.target.value"
            />

            <button class="btn btn-outline-dark" type="submit" @click="addMovies">Add</button>
         </form>
    </div>
</template>
<script>
export default {
    data(){
        return{
            name:'',
            view:''
        }
    },
    methods:{
        addMovies(){
            if(!this.name || !this.view) return
            const newMovie =  {
                id: new Date(),
                name:this.name,
                view:this.view
            }
            
            this.$emit('createMovie', newMovie);
            this.name = '';
            this.view = '';
        }

    }
}
</script>
<style scoped>
    
</style>