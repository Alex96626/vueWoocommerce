<template>
  <label for="search">
    <span>Найди меня полностью</span>
    <input
    v-model = "value"
    @input="$emit('input', value)"
    type="text" name="search" id="search" />
  </label>
</template>

<script>
export default {
  name: 'SearchElement',
  data() {
    return {
      value: '',
    };
  },

  methods: {
  },
};
</script>
