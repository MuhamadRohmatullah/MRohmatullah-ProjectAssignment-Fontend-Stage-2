<template>
        <div class="row navbar bg-warning mb-0" style="width:auto">
            <div class="col-xl-10 text-start">
                <h2 class="fw-bold">Inosoft Store</h2>
            </div>
            <div class="col-xl-1 text-end pe-0 me-0">
                <div class="form-check form-switch">
                <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckDefault">
                <label class="form-check-label" for="flexSwitchCheckDefault"></label>
                </div>
            </div>
            <div class="col-xl-1 mt-2 ps-0 ms-0">
                <chart-icon @click="remov()" :min="crt" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasScrolling" aria-controls="offcanvasScrolling" id="ichart"/>{{count}}
            </div>
        </div>
</template>
<script>
export default {
    props:{
        count:{
            type:Number,
            default:null
        },
        crt:{
            type:Number,
            default: 0
        }
    },
    methods:{
        remov(){
            document.getElementById('ichart').removeAttribute('data-bs-toggle', 'data-bs-target')
        }
    }
}
</script>