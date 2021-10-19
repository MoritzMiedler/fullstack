<template>
  <div>
    <CarCards :cardata="cars"></CarCards>
  </div>
</template>

<script>
import CarCards from "@/components/CarCards.vue";

export default {
  components: {
    CarCards
  },
  props: {
    cars: {
      type: Array
    }
  }
};
</script>

<style lang="css" scoped></style>
