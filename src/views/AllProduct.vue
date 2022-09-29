<template>
    <Header title="All Product Page" subtitle="Say Something"/>
    <!-- Section-->
    <section class="py-5">
        <div class="container px-4 px-lg-5 mt-5">
            <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-5 justify-content-center">
                <div class="col mb-5" v-for="(row,index) in products" :key="index">
                    <Card :product="row"/>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import Header from '@/components/header.vue';
import Card from '@/components/card.vue';
const axios = require('axios');

export default {
    name: "AllProduct",
    data() {
        return {
            products: [],
        };
    },
    mounted() {
        axios.get("https://fakestoreapi.com/products")
            .then(response => {
            console.log(response);
            this.products = response.data;
        });
    },
    components: { Header, Card }
}
</script>

<style>

</style>