<template>
  <div>
    <div class="container">
      <div
        v-if="arrCard.length === 10"
        class="row row-cols-5 gap-4"
      >
        <CardCharter
          v-for="card in arrCard"
          :key="card.title"
          class="card-color text-center"
          :img-url="card.poster"
          :title="card.title"
          :author="card.author"
          :year="card.year"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CardCharter from '@/components/CardCharter.vue';

export default {
  name: 'PageMain',
  components: {
    CardCharter,
  },
  data() {
    return {
      arrCard: null,
      urlApi: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        console.log(axiosResponse);
        this.arrCard = axiosResponse.data.response;
      });
  },
};
</script>

<style lang="scss" scoped>
  div {
    background-color: #1E2D3B;
    .container{
      width: 1000px;
      margin: 0 auto;
      padding: 4em 0;
      div{
        .card-color{
          color: white;
        }
    }
    }
  }
</style>
