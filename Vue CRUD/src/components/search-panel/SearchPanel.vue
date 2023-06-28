<template>
    <input type="text" class="form-control search-input" @input="onInput"  placeholder="search movies..." />
</template>

<script>
export default {
    data(){
        return{
            term:''
        }
    },
    methods: {
        onInput(e){
           this.term = e.target.value
           this.$emit('onUpdate', this.term)

        }
    },
}
</script>

<style scoped>
.search-input{
    margin-top: 2rem;
    padding: 1rem;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
    background-color: #fcfaf5;
}
</style>