<template>
    <div class="products-container">
        <div v-for="product in products" :key="product.id">
            <product
                :product="product"
                v-on:product-added="addProductToList($event)"
            />
        </div>

        <span>{{ productsQuanties }}</span>

        <input type="text" v-model="testString" />
        <span>{{ testString }}</span>

        <button @click="changeValue">change obj value</button>
    </div>
</template>

<script>
import Product from "./product-component.vue";
export default {
    components: { Product },
    data() {
        return {
            products: [],
            cartProducts: [],
            testString: "",
            watchObj: {
                name: "X1",
                test: "whatever",
            },
        };
    },
    computed: {
        productsQuanties() {
            console.log("computed");
            return this.cartProducts.length;
        },
    },
    watch: {
        testString(newVal, oldVal) {
            if (newVal.length > 3) {
                this.testString = oldVal;
            }
        },
        cartProducts: {
            deep: true,
            handler(newVal, oldVal) {
                console.log(`old: ${oldVal}`);
                console.log(`new: ${newVal}`);
            },
        },

        "watchObj.test"(newVal, oldVal) {
            console.log(`old: ${oldVal}`);
            console.log(`new: ${newVal}`);
        },
    },
    methods: {
        getProducts() {
            fetch(
                "https://internship-products-func.azurewebsites.net/api/GetProducts"
            )
                .then((result) => result.json())
                .then((prods) => (this.products = prods));
        },

        addProductToList(e) {
            console.log(e);
            this.cartProducts.push(e);
        },

        changeValue() {
            this.watchObj.test = "";
        },
    },
    created() {
        this.getProducts();
    },
};
</script>