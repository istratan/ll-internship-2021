<template>
    <div>
        <div class="product-card">
            <img
                :src="product.productImageUrl"
                class="product-image"
            /><br /><span>{{ product.productName | capitalizeText }}</span
            ><br /><span>In stock: {{ product.isInStock }}</span
            ><br /><span>{{ product.price }} {{ product.currency }}</span
            ><br /><button type="button" class="btn" @click="addToCart">
                Add to cart
            </button>
        </div>
    </div>
</template>

<script>
export default {
    props: ["product"],
    methods: {
        addToCart() {
            const payload = {
                name: this.product.productName,
                price: this.product.price,
            };

            this.$emit("product-added", payload);
        },
    },
    filters: {
        capitalizeText(text) {
            return text.toLowerCase();
        },
    },
};
</script>