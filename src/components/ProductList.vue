<template>
    <div>
        <h1>{{ msg }}</h1>

        <ul v-if="products.length" class="list">
            <Product v-for="product in products" v-bind:product="product" @onRemoveProduct="handleRemoveProduct"/>
        </ul>

        <p v-else>No products!</p>

        <md-button class="md-dense md-raised md-accent" v-on:click="removeLastItem()">Remove last item</md-button>
        <md-button class="md-dense md-raised md-primary" v-on:click="sortList()">Sort products</md-button>
    </div>
</template>

<script>
    import 'vue-material/dist/vue-material.min.css'
    import 'vue-material/dist/theme/default.css'
    import Product from './Product';
    import Vue from 'vue';
    import { MdButton } from 'vue-material/dist/components'

    Vue.use(MdButton);

    export default {
        name: 'ProductList',
        props: {
            msg: String,
            products: {
                type: Array,
            }
        },
        components: {
            Product
        },
        methods: {
            removeLastItem() {
                this.products.pop();
            },

            handleRemoveProduct(id) {
                this.products.splice(this.products.indexOf(id), 1);
            },

            sortList() {
                return this.products.sort((a, b) => a.name > b.name );
            }
        }
    }
</script>

<style scoped>
    .list {
        list-style: none;
    }

    button {
        margin: 0 10px;
    }
</style>
