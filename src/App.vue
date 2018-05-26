<template>
    <div id="app">
        <img src="./assets/logo.png">

        <ProductList msg="Product list injected from App.js" :products="products"/>

        <add-product @onAddProduct="handleAddProduct"></add-product>
    </div>
</template>

<script>
    import AddProduct from './components/AddProduct';
    import ProductList from './components/ProductList';
    import VeeValidate from 'vee-validate';
    import Vue from 'vue';

    Vue.use(VeeValidate);

    export default {
        name: 'app',
        components: {
            AddProduct,
            ProductList
        },
        data() {
            return {
                products: [{
                    id: 0,
                    name: 'Pizza'
                }, {
                    id: 1,
                    name: 'Burger'
                }, {
                    id: 1,
                    name: 'Orange juice'
                }]
            }
        },
        methods: {
            handleAddProduct(product) {
                this.products.push(product);
            }
        }
    }
</script>

<style>
    #app {
        -moz-osx-font-smoothing: grayscale;
        -webkit-font-smoothing: antialiased;
        color: #2c3e50;
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        margin-top: 60px;
        text-align: center;
    }
</style>
