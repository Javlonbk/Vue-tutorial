<template >
    <li class="
    list-group-item d-flex justify-content-between"
    :class="[{like: movie.like}, {favorite: movie.favorite}]"
    >
            <span @click="$emit('onToggle', {id: movie.id, prop: 'like'})" class="list-group-item-label">{{movie.name}}</span>
            <input type="number" class="list-group-item-input" :value="movie.view">

            <div class="d-flex justify-content-center align-items-center">
                <button type="button" class="btn-like btn-sm">
                    <i class="bi bi-heart-fill"></i>
                </button>
                <button type="button" class="btn-star btn-sm" @click="$emit('onToggle', {id: movie.id, prop: 'favorite'})">
                    <i class="bi bi-star-fill"></i>
                </button>
                <button type="button" class="btn-trash btn-sm" @click="$emit('onDelete', movie.id)">
                    <i class="bi bi-trash-fill"></i>
                </button>
            </div>
        </li>
</template>
<script>
export default {
        props:{
            movie:{
                type: Object,
                required: true
            }
        },
        methods:{
            onLike(){
                this.$emit("onLike", this.movie.id)
            }
        }
}
</script>
<style scoped>
 .list-group-item{
        padding: 10px 15px;
        border: none;
        border-bottom: 1px solid #3d5a80;
    }
    .list-group-item span{
        line-height: 35px;
        font-size: 20px;
        cursor: pointer;
        width: 550px;
        color: black;
    }
    .list-group-item input{
        line-height: 35px;
        font-size: 20px;
        text-align: center;
        border: none;
        outline: none;
    }
    .list-group-item button{
        width: 35px;
        height: 35px;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 2px;
        font-size: 1rem;
        border: none;
        cursor: pointer;
    }
    .list-group-item .btn-like{
       color: red;
       transition: 0.3s all;
       transform: translateX(50px);
       opacity: 0;
    }
    .list-group-item.like .btn-like{
        transform: translateX(0);
        opacity: 1;

    }
    .list-group-item .btn-star{
        color: #fff;
    }
    .list-group-item.favorite .btn-star, span{
        color: #ffd700;

    }
    .list-group-item .btn-trash{
        color: #3d5a80;
    }
</style>