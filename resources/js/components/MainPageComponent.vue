<template>
    <h2>Semua Product</h2>
    <product :list="food" @emit-addChart="addToChart"/>
    <chart :foodList="food" :numIndex="param"/>
</template>
<script>
export default {
    data(){
        return{
            food:[
                {
                    name: "Indomie Goreng Rendang",
                    description: "Masakan instan terenak di dunia",
                    stok: 10,
                    price: 3900
                },
                {
                    name: "Mie Gelas Rendang",
                    description: "Mie instant khusus anak kosan",
                    stok: 3,
                    price: 1500
                },
                {
                    name: "Bakmi mewah",
                    description: "kalau anak kosan jangan macam2 deh",
                    stok: 80,
                    price: 10000
                }
            ],
            param : null

        }
    },
    methods:{
        addToChart(index){
            this.param = index
        }
    }
}
</script>