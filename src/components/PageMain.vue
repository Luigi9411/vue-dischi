<template>
  <div>
    <div class="container">
      <div
        v-if="arrCard.length === 10"
        class="row row-cols-5 gap-4"
      >
        <CardCharter
          v-for="card in arrDiscs"
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
  props: {
    genreFilter: String,
  },
  data() {
    return {
      arrCard: null,
      urlApi: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  computed: {
    arrMusic() {
      const arrMusic = [];
      if (this.arrCard) {
        this.arrCard.forEach((objCard) => {
          if (!arrMusic.includes(objCard.genre)) {
            arrMusic.push(objCard.genre);
          }
        });
      }
      console.log(arrMusic);
      return arrMusic;
    },
    arrDiscs() {
      if (this.genreFilter === 'all') {
        return this.arrCard;
      }
      return this.arrCard.filter((objCard) => objCard.genre === this.genreFilter);
    },
  },
  watch: {
    arrMusic(newValue, oldValue) {
      console.log(newValue, oldValue);
      this.$emit('genresReady', newValue);
    },
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
      min-height: 90vh;
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
