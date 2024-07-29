<template>
    <div>
        <h2>Products</h2>
        <div class="grid grid-cols-4 gap-5">
            <div v-for="p in products">
                <ProductCard :product="p" />
            </div>
        </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'products'
})

const response = await useFetch('https://fakestoreapi.com/products')
console.log(response);
const products = response.data;
console.log(products.value[0]);
</script>

<style lang="scss" scoped></style>