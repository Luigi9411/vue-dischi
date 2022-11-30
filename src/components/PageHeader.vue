<template>
  <div>
    <img
      src="../../public/img/spotify-logo.webp"
      class="logo img-fluid"
      alt="error"
    >
    <label for="select-music">
      <select
        id="select-music"
        v-model="genreFilter"
        name="genre"
        @change="genreChange"
      >
        <option value="all">
          All
        </option>
        <option
          v-for="genre in genresList "
          :key="genre"
          :value="genre"
        >
          {{ genre }}
        </option>
      </select>
    </label>
  </div>
</template>

<script>

export default {
  name: 'PageHeader',
  props: {
    genresList: Array,
  },
  data() {
    return {
      genreFilter: 'all',
    };
  },
  methods: {
    genreChange() {
      this.$emit('changedGenre', this.genreFilter);
    },
  },
};

</script>

<style lang="scss" scoped>
    div{
      height: 10vh;
      background-color: #2E3A46;
      display: flex;
      justify-content: space-between;
      .logo{
        align-self: center;
        width: 3%;
        margin: 0 1em;
      }
      label{
         padding-right: 2em;
         align-self: center;
      }
    }
</style>
