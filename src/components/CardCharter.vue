<template>
  <div class="col-1">
    <div>
      <img
        :src="imgUrl"
        :alt="error"
        class="img-card"
      >
      <h2 class="title fs-5">
        {{ title }}
      </h2>
      <p class="author">
        {{ author }}
      </p>
      <p class="year">
        {{ year }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardCharter',
  props: {
    imgUrl: String,
    title: String,
    author: String,
    year: String,
  },
};
</script>

<style  lang="scss" scoped>
  .col-1{
    width: 180px;
    height: 310px;
    padding: 1em 1em;
    background-color: #2E3A46;
    .img-card{
      width: 100%;
    }
    .title{
      text-transform: uppercase;
      margin-bottom: 1em;
      margin-top:.5em;
    }
    .author{
      line-height: .1em;
      color: #757E83;
    }
    .year{
      line-height: .2em;
      color: #757E83;
    }
  }
</style>
