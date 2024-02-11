<template>

 <div class="container-fluid py-1">  
 <div class="row p-0">
    <div v-for="(prod, index) in list" :key="index" class="col-3 m-0 p-1">
    <div class="card shadow-sm" style="width : auto">
      <div class="card-body text-center p-0 m-0">
         <img src="{{ mix('public/img/1.jpg') }}" alt="" style="width : auto">
         <h5 class="fw-bold">{{prod.name}}</h5>
         <h6>{{prod.description}}</h6>
      </div>
      <div class="card-footer text-center p-0 m-0">
        <h6>Stok: {{ prod.stok }}</h6>
        <h6 v-if="prod.stok != 0">Price: Rp.{{ prod.price }}</h6>
        <h6 v-else style="text-decoration : line-through">Price: Rp.{{ prod.price }}</h6>
        <button v-if="prod.stok == 0" class="btn btn-danger mb-1" type="button" @click="test(index)">Sold Out</button>
        <button v-else class="btn btn-primary mb-1" @click="addChart(index, prod)" type="button">Add to chart</button>
      </div>
   </div>
    </div>
 </div>
 </div>

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
            nom: null,
            p: null,
            chart: []
        }
    },
    methods:{
        addChart(index, prod){
            this.p+=1
            this.$emit('emit-addChart', index, this.p)
            prod.stok-=1
        },
    }
});
</script>
<style>

.card{
    border-radius: 0;
}

.sold{
    background-color: rgba(255, 255, 255, 0.397);
}
</style>