<template>
    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>Quantity</th>
                <th>Price</th>
            </tr>
        </thead> 
        <tbody v-for="(flist, index) in foodList" :key="index">
            <tr v-if="index == numIndex">
                <td>{{ flist.name }}</td>
                <td>{{ flist.stock }}</td>
                <td>{{ flist.price }}</td>
                <td><button>Delete</button></td>
            </tr>
        </tbody>
        <tr>
            <td>Total</td>
            <td> </td>
            <td>Rp.{{ }} </td>
        </tr>
        <tr>
            <td><button>Checkout</button></td>
        </tr>
    </table>
</template>
<script>
export default({
    props:{
        foodList:{
            type:Array,
            default:() => {
                return []
            }
        },
        numIndex:{
            type:Number,
            default: null
        }
    }
})
</script>
