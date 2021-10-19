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
import CarCard from "@/components/CarCard.vue";

export default {
  data() {
    return {};
  },
  props: {
    cardata: {
      type: Array
    }
  },
  components: {
    CarCard
  }
};
</script>

<style lang="scss" scoped></style>
