<template>

    <div class="modal fade" id="exampleModalToggle" aria-hidden="true" aria-labelledby="exampleModalToggleLabel" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
        <div class="modal-header">
            <h1 class="modal-title fs-5" id="exampleModalToggleLabel">Modal 1</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
           Rp. {{total}}
        </div>
        <div class="modal-footer">
            <button class="btn btn-primary" data-bs-target="#exampleModalToggle2" data-bs-toggle="modal">Open second modal</button>
        </div>
        </div>
    </div>
    </div>
    <div class="modal fade" id="exampleModalToggle2" aria-hidden="true" aria-labelledby="exampleModalToggleLabel2" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
        <div class="modal-header">
            <h1 class="modal-title fs-5" id="exampleModalToggleLabel2">Modal 2</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
           Belum tersedia fitur lanjutan
        </div>
        <div class="modal-footer">
            <button class="btn btn-primary" data-bs-target="#exampleModalToggle" data-bs-toggle="modal">Back to first</button>
        </div>
        </div>
    </div>
    </div>

    <div class="offcanvas offcanvas-bottom offcanvas-size-xl"  data-bs-scroll="true" data-bs-backdrop="false" tabindex="-1" id="offcanvasScrolling" aria-labelledby="offcanvasScrollingLabel">
    <div class="offcanvas-header mt-0 mb-0 p-0">
        <div class="row mt-1 ms-1 pe-1">
            <div class="col">
                <chart-icon :max="cnth"/>
            </div>
            <div class="col text-start">
                <h3>Keranjang</h3>
            </div>
        </div>
        <button @click="reAdd()" type="button" class="btn-close me-2" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body mt-0 p-0">
        <table class="table table-hover mt-0 p-0">
            <thead>
                <tr>
                    <th scope="col">Name</th>
                    <th scope="col">Quantity</th>
                    <th scope="col">Price</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(list, index) in listChart" :key="index">
                    <td>{{ list.name }}</td>
                    <td>{{ s }}</td>
                    <td>{{ functionPrice(list, s) }}</td>
                    <td><button class="btn btn-danger" @click="deleteAr(index)">Delete</button></td>
                </tr>
            </tbody>
            
        </table>
    </div>
    <div class="offcanvas-footer">
        <table class="table ms-2">
            <tr>
                <td class="fw-bold">Total Rp.{{ this.total }} </td>
                <td class="text-end me-5 pe-5 pt-1">
                    <button class="btn btn-primary" data-bs-target="#exampleModalToggle" data-bs-toggle="modal">Checkout</button>
                </td>
            </tr>
        </table>
    </div>
    </div>

</template>
<script>
export default({
    emits:['delete-emit'],
    props:{
        foodList:{
            type:Array,
            default:() => {
                return []
            }
        },
        cnt:{
            type:Number,
            default:null
        },
        listChart:{
            type:Array,
            default:()=>{
                return []
            }
        },
        numIndex :{
            type:Number,
            default: null
        },
        s:{
            type:Number,
            default: null
        }
    },
    data(){
        return{
            c: 0,
            cnth:1,
            total: null
        }
    },
    methods:{
        reAdd(){
            document.getElementById('ichart').setAttribute("data-bs-toggle","offcanvas")
             document.getElementById('ichart').setAttribute("data-bs-target","#offcanvasScrolling")
        },
        deleteAr(index){
            this.$emit('delete-emit', index)
            this.listChart.splice(index, 1)
        },
        functionPrice(list, s){
            this.total = list.price*s
            return this.total
        }
    },
    mounted(){
    
    }
})
</script>
<style>

.offcanvass, .offcanvas-size-xl{
     --bs-offcanvas-height: 47vh !important;
}

.offcanvas-footer{
    border-top: 1px solid rgb(201, 197, 197);
}
</style>