<template>
    <form @submit.prevent="onSubmit()">
        <input name="product" v-model="newProduct.name" type="text" v-validate="'required|min:3'">

        <button>Add hardcoded text</button>

        <div v-show="errors.has('product')">
            {{ errors.first('product') }}
        </div>
    </form>
</template>


<script>
    export default {
        name: 'AddProduct',
        data() {
            return {
                newProduct: {
                    name: ''
                }
            }
        },
        methods: {
            onSubmit() {
                this.$validator.validateAll().then(result => {
                    if (!result) {
                        return;
                    }

                    this.$emit('onAddProduct', {
                        id: Date.now(),
                        ...this.newProduct
                    });

                    this.newProduct.name = '';
                    this.$validator.reset();
                });
            }
        }
    }
</script>

<style scoped>
    form {
        margin-top: 20px;
    }

    form button {
        margin-left: 10px;
    }
</style>
