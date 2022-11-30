<template>
  <div>
    <PageHeader
      :genres-list="genresList"
      @changedGenre="genreChange"
    />
    <PageMain
      :genre-filter="genreFilter"
      @genresReady="getGenrestList"
    />
  </div>
</template>

<script>

import PageHeader from '@/components/PageHeader.vue';

import PageMain from '@/components/PageMain.vue';

export default {
  components: {
    PageHeader,
    PageMain,
  },
  data() {
    return {
      genresList: [],
      genreFilter: 'all',
    };
  },
  methods: {
    getGenrestList(genresList) {
      this.genresList = genresList;
    },
    genreChange(genreFilter) {
      this.genreFilter = genreFilter;
    },
  },
};
</script>

<style lang="scss">
   @import "../node_modules/bootstrap/scss/bootstrap";
   @import url('https://fonts.googleapis.com/css2?family=Lato&family=Roboto&display=swap');

   body {
     font-family: 'Lato', sans-serif;
   }
</style>
