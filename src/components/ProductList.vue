<template>
    <div>
        <h1>{{ msg }}</h1>

        <ul v-if="products.length" class="list">
            <Product v-for="product in products" v-bind:product="product" @onRemoveProduct="handleRemoveProduct"/>
        </ul>

        <p v-else>No products!</p>

        <button v-on:click="removeLastItem()">Remove last item</button>
        <button v-on:click="sortList()">Sort products</button>
    </div>
</template>

<script>
    import Product from './Product';

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
        margin: 0 5px;
    }
</style>
