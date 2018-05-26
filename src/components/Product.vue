<template>
    <li>{{ product.name }} <button v-on:click="removeCurrent(product)">Usuń</button></li>
</template>

<script>
    export default {
        name: 'Product',
        props: {
            product: Object
        },
        methods: {
            removeCurrent(product) {
                this.$emit('onRemoveProduct', {
                    id: product.id,
                });
            }
        }
    }
</script>
