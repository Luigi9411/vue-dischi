<template>
  <div>
    <img
      src="../../public/img/spotify-logo.webp"
      class="logo img-fluid"
      alt="error"
    >
  </div>
</template>

<script>
export default {
  name: 'PageHeader',
};

</script>

<style lang="scss" scoped>
    div{
      height: 10vh;
      background-color: #2E3A46;
      display: flex;
      .logo{
        align-self: center;
        width: 3%;
        margin: 0 1em;
      }
    }
</style>
