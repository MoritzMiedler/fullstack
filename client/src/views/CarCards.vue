<template>
  <v-row class="d-flex flex-wrap"
    ><CarCard
      class="ma-5 d-flex flex-column justify-end"
      style="width:400px"
      v-for="(car, i) in cardata"
      :key="i"
      :cardata="car"
      @buyCar="buyCar($event)"
    ></CarCard
  ></v-row>
</template>

<script>
import CarCard from '@/views/CarCard.vue';
import axios from 'axios';
export default {
  data() {
    return {
      cardata: [],
    };
  },
  components: {
    CarCard,
  },
  methods: {
    async getCars() {
      const cars = await axios({ method: 'GET', url: 'http://127.0.0.1:3000/cars' });

      this.cardata = cars.data;
    },
    async buyCar(event) {
      event.title += ' RESERVED!';
      await axios({
        method: 'PATCH',
        url: 'http://127.0.0.1:3000/cars/' + event.id,
        'content-type': 'application/json',
        data: event,
      });
    },
  },

  created() {
    this.getCars();
  },
};
</script>

<style lang="scss" scoped></style>
