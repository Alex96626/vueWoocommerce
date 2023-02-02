<template>
    <ul class="pagination">
        <li class="pagination__item pagination__prev"
          v-if="page > 1"
        >
        <button class="button"
          @click.prevent = showPrevPage
        >Назад</button>
        </li>
        <li class="pagination__item pagination__next"
          v-if="!(this.element.length / 6 <= this.page)"
        >
        <button class="button"
          @click.prevent = showNextPage>
        Вперед</button>
        </li>
    </ul>
</template>

<script>
export default {
  name: 'AddPagination',
  data() {
    return {
      firsPage: true,
    };
  },

  methods: {
    showNextPage() {
      const newCountPage = this.page + 1;
      this.$emit('click', newCountPage);
    },

    showPrevPage() {
      const newCountPage = this.page - 1;
      this.$emit('click', newCountPage);
    },
  },

  props: {
    page: Number, // счетчик текущей страницы
    element: Array, // массив слайдов
  },
};
</script>
