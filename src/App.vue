<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png" />
        <product-list />
    </div>
</template>


<script>
import ProductList from "./components/product-list.vue";

export default {
    name: "App",
    components: { ProductList },
    data() {
        return {};
    },
    methods: {},
};
</script>

<style>
body {
    background-color: #e9e9e9;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

.products-container {
    display: grid;
    grid-gap: 1rem;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
}

.product-image {
    max-width: 230px;
}

.product-card {
    display: flex;
    flex-direction: column;
    padding: 1rem;
    height: 420px;
    margin: 5px;
    background-color: white;
    box-shadow: 5px 5px 5px lightgray;
    justify-content: space-between;
    max-width: 230px;
}

.logo-img {
    margin-bottom: 2rem;
}

.btn {
    background-color: #41b883;
    border: none;
    color: white;
    padding: 15px 68px;
    text-align: left;
    font-size: 16px;
    display: flex;
    justify-content: flex-end;
}
</style>