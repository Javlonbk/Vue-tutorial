<template>
    <div class="btn btn-group">
        <button 
        v-for="btn in btns" 
        :key="btn.title" 
        class="btn"  type="button" 
        :class="[filter == btn.type ? 'btn-dark': 'btn-outline-dark']"
        @click="clickBtn(`${btn.type}`)">
        {{ btn.title }}
        </button>
    </div>
</template>
<script>
export default {
    data(){
       return{
        btns: [
            {
                type:'all',
                title:'All'
            },
            {
                type:'favorite',
                title:'Famous'
            },
            {
                type:'mostView',
                title:'Most viewed'
            }
        ],
        filter: 'all'
       } 
    },
    methods:{
        clickBtn(val){
            this.filter = val
            this.$emit('onFilter', this.filter)
        }
    }
}
</script>
<style scoped>
    
</style>