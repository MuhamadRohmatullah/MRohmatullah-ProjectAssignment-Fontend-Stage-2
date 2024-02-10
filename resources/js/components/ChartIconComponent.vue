<template>
    <button class="btn btn-primary">Chart</button>
</template>
<script>

export default {
    props:{
        c:{
            type:Number,
            default: null
        },
        min:{
            type:Number,
            default: 0
        }
    },
    methods:{
        functionChart(){
                 return this.c
    }
    },
    data(){
        return{
            num : null
        }
    }
} 
</script>
