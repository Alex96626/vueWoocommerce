<template>
    <div class="left-bar">
        <form action="" class="form form-add-product" id="new-product">
            <label for="product-name" class="form__label">
                <span class="form__title">Наименование товара</span>
                <input type="text" name="product-name"
                placeholder="Введите наименование товара"
                class="form__field"
                v-model="newProduct.name">
            </label>
            <label for="product-description" class="form__label">
                <span class="form__title">Описание товара</span>
                <textarea name="product-description"
                placeholder="Введите описание товара"
                class="form__field" rows="6"
                v-model="newProduct.description"> </textarea>
            </label>
            <P>{{ newProduct.productName }}</P>
            <label for="product-image-src" class="form__label">
                <span class="form__title">Ссылка на изображение товара</span>
                <input type="text" name="product-image-src"
                placeholder="Введите ссылку"
                class="form__field">
            </label>
            <label for="product-price" class="form__label">
                <span class="form__title">Цена товара</span>
                <input type="text" name="product-price"
                placeholder="Введите цену"
                class="form__field"
                v-model="newProduct.price">
            </label>
            <button
            v-on:click.prevent = createNewProduct
            class="button form-add-product__button"
            >Добавить товар</button>
        </form>
    </div>
</template>

<script>
export default {
  name: 'AddProduct',
  data() {
    return {
      newProduct: {
        name: '',
        description: '',
        price: '',
      },
    };
  },

  methods: {
    createNewProduct() {
      this.$emit('click', this.newProduct);
      this.newProduct = {
        name: '',
        description: '',
        price: '',
      };
    },
  },

};
</script>
