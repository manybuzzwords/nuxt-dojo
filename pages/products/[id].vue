<!-- /products/:id e.g. /products/123-->

<template>
    <div>
        <ProductDetails :product="product" />
    </div>
</template>

<script setup>
const { id } = useRoute().params;
const uri = 'https://fakestoreapi.com/products/' + id; 

definePageMeta({
    layout: 'products'
})

const { data: product } = await useFetch(uri, { key: id })

if (!product.value) {
    throw createError({
        statusCode: 404,
        statusMessage: 'Product not found: ' + id,
        fatal: true
    })
}

// const product = data
</script>
<style scoped>

</style>