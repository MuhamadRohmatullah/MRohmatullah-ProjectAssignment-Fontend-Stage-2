<template>
    <table>
        <tr>
            <th>Name</th>
            <th>Description</th>
            <th>Stock</th>
            <th>Price</th>
        </tr>
        <tr v-for="(prod, index) in list" :key="index">
            <td>{{ prod.name }}</td>
            <td>{{ prod.description }}</td>
            <td>{{ prod.stok }}</td>
            <td>Rp. {{ prod.price }}</td>
            <td><button @click="addChart(index)">Add to chart</button></td>
        </tr>
    </table>

</template>
<script>

export default({
    emits:['emit-addChart'],
    props:{
        list:{
            type:Array,
            default:() => {
                return []
            }
        }
    },
    data(){
        return{
            nom: null
        }
    },
    methods:{
        addChart(index){
            this.$emit('emit-addChart', index)
        }
    }


});

</script>
