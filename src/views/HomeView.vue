<template>
  <div class='container' style='display: flex; gap: 16px'>
    <AddProduct @click='addNewProduct'></AddProduct>
    <div class='products'>
      <div class='products__header'>
        <AddPagination
          :page='this.countPage'
          :element='filteredProducts'
          @click='showNewPage'>
        </AddPagination>
        <Order
          @selected="getFilterResult"
        >
        </Order>
        <Search
          @input="getSearchValue"
        ></Search>
      </div>
      <div class='products__list'>
        <Product
          v-for='(product, index) in modifyProductsList'
          :key='index'
          :product='product'
        >
        </Product>
      </div>
    </div>
  </div>
</template>
<script>
// @ is an alias to /src
import AddProduct from '@/components/AddProduct.vue';
import AddPagination from '@/components/Pagination.vue';
import Order from '@/components/Order.vue';
import Search from '@/components/Search.vue';
import Product from '@/components/Product.vue';

export default {
  name: 'HomeView',
  components: {
    AddProduct,
    AddPagination,
    Order,
    Search,
    Product,
  },
  data() {
    return {
      // products: [],
      products: [
        {
          name: 'test2',
          description: 'bla bla',
          price: '11000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '12000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '13000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '14000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '15000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '16000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '17000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '18000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '19000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '20000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '21000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '22000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '23000',
        },
        {
          name: 'test1',
          description: 'bla bla',
          price: '24000',
        },
      ],
      countPage: 1,
      serchValue: '',
      filterValue: '',
    };
  },

  created() {
    const productData = localStorage.getItem('products');
    if (!productData) return;
    this.products = JSON.parse(productData);
  },

  computed: {
    getStartCountElement() {
      return this.countPage * 6 - 6;
    },

    getEndCountElement() {
      return this.countPage * 6;
    },

    modifyProductsList() {
      return this.filteredProducts.slice(this.getStartCountElement, this.getEndCountElement);
    },

    filteredProducts() {
      const products = [...this.products];
      let result = products;
      if (!this.serchValue && !this.filterValue) return products;
      // фильтр по поиску
      if (this.serchValue) {
        result = result.filter((item) => item.name === this.serchValue);
      }
      if (this.filterValue) {
        // фильтр по цене
        if (this.filterValue === 'max-price') {
          result = result.sort((a, b) => (a.price > b.price ? 1 : -1));
        } else {
          result = result.sort((a, b) => (a.price < b.price ? 1 : -1));
        }
        return result;
      }
      return result;
    },
  },

  methods: {
    addNewProduct(newProduct) {
      this.products.push(newProduct);
      localStorage.setItem('products', JSON.stringify(this.products));
    },

    showNewPage(newCountPage) {
      this.countPage = newCountPage;
    },

    getSearchValue(value) {
      this.serchValue = value;
    },

    getFilterResult(name) {
      this.filterValue = name;
    },
  },
};
</script>
