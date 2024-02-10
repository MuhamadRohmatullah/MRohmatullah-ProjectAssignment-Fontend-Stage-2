<template>
    <navigasi :count="c" :crt="cls"/>
    <h5 class="ms-3 mb-0 p-0">Semua Product</h5>
    <product :list="food" @emit-addChart="addToChart"/>
    <chart :foodList="food" @delete-emit="deleteIcon" :listChart="param"/>
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
                    stok: 20,
                    price: 1500
                },
                {
                    name: "Bakmi mewah",
                    description: "kalau anak kosan jangan macam2 deh",
                    stok: 80,
                    price: 10000
                },
                {
                    name: "Super Bubur",
                    description: "sarapan cepat tanpa ribet",
                    stok: 50,
                    price: 2500
                }
            ],
            param : [ ],
            c: null,
            cls: 0

        }
    },
    methods:{
        addToChart(index, p){
            let ps = {
                id: index,
                name: this.food[index].name,
                stok: 1,
                price: this.food[index].price
            }
            this.param.push(ps)
            this.c=p
        },
        deleteIcon(index){
            this.c-=1
        }
    }
}
</script>