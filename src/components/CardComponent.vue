<template>
  <div>
    <img :src="product.image" class="product-img">
    <h4 @click="$emit('modalOpen')">{{product.title}}</h4>
    <p>{{product.price}} 원</p>
  </div>
</template>

<script>
export default {
    name: 'CardComponent',
    props: {
        product : Object
    }
}
</script>

<style>
.product-img{
    width: 100%;
    margin-top: 40px;
}
</style>