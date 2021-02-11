<template>
  <div>
    <h1>Product Title: {{ product_title }}</h1>
    <h2>Price: {{ price }}</h2>
    <p>Path: {{ $route.path }}</p>
    <NuxtLink to="/">Back to Honepage</NuxtLink>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect }) {
    const items = await fetch(
      'http://localhost:3005/api/coupon'
    ).then((res) => res.json())

    const filteredItem = items.find(
      (el) =>
        el.product_title.toLowerCase() === params.product_title
    )
    if (filteredItem) {
      return {
        product_title: filteredItem.product_title,
        price: filteredItem.price
      }
    } else {
      redirect('/')
    }
  }
}
</script>
