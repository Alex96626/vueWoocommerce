<template>
      <div class="product">
        <img src="@/assets/images/product.jpg" alt="" class="product__picture product__item">
        <h3 class="product__name product__item">{{ product.name }}</h3>
        <p class="product__description product__item">{{ product.description }}</p>
        <div class="product__footer product__item">
          <div class="product__price ">{{ product.price }}</div>
        </div>
      </div>
</template>

<script>
export default {
  name: 'ProductInfo',
  props: ['product'],
};
</script>
