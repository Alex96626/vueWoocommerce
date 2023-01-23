<script>
// @ is an alias to /src
import AddProduct from '@/components/AddProduct.vue';
import Product from '@/components/Product.vue';

export default {
  name: 'HomeView',
  components: {
    AddProduct,
    Product,
  },
  data() {
    return {
      products: [
        {
          name: 'test',
          description: 'Прикольный товар и бла бла бла',
          price: 10000,
          currency: 'руб',
        },
        {
          name: 'test2',
          description: 'test-description',
          price: 10000,
          currency: 'руб',
        },
        {
          name: 'test3',
          description: 'test-description',
          price: 10000,
          currency: 'руб',
        },
        {
          name: 'test4',
          description: 'test-description',
          price: 10000,
          currency: 'руб',
        },
      ],
    };
  },

  provide() {
    return {
      products: this.products,
    };
  },

};
</script>
<template>
  <div class="container" style="display:flex; gap:16px">
    <AddProduct></AddProduct>
    <div class="products">
      <Product
        v-for="product in products"
        :key="product.name"
        v-bind:product="product"
        >
      </Product>
    </div>
  </div>
</template>
