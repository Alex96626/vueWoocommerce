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
      products: [],
    };
  },

  created() {
    const productData = localStorage.getItem('products');
    if (productData) {
      this.products = JSON.parse(productData);
    }
  },

  methods: {
    showNewProduct(newProduct) {
      console.log(newProduct);
      this.products.push(newProduct);
      localStorage.setItem('products', JSON.stringify(this.products));
    },
  },

};
</script>
<template>
  <div class="container" style="display:flex; gap:16px">
    <AddProduct
    @click="showNewProduct"
    ></AddProduct>
    <div class="products">
      <Product
        v-for="product in products"
        :key="products[product.length - 1]"
        v-bind:product="product"
        >
      </Product>
    </div>
  </div>
</template>
