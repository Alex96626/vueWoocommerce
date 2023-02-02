<template>
    <label for="filter">
      <select name="filter" id="product-filter"
      v-model="value"
      @change="$emit('selected', value)"
      >
        <option value="defult" disabled>Фильтр товаров</option>
        <option value="max-price">По возростанию</option>
        <option value="min-price">По убыванию</option>
      </select>
    </label>
  </template>
<script>
export default {
  name: 'FilterElemtns',
  data() {
    return {
      value: '',
    };
  },

};
</script>
