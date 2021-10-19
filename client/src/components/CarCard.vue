<template>
  <v-card>
    <v-img :src="cardata.image"></v-img>

    <div class="pa-3">
      <span class="text-h5"
        >{{ cardata.title }}<span v-if="cardata.status == 'sold'">*RESERVED*</span></span
      >
      <br />
      Owner:
      <span class="font-weight-bold"
        >{{ cardata.owner.firstName }} {{ cardata.owner.lastName }}</span
      >
      <br />
      Year: <span class="font-weight-bold">{{ cardata.yearOfMake }}</span>
      <br />
      Miles: <span class="font-weight-bold">{{ cardata.miles }} </span>
      <br />
      Price:
      <span class="font-weight-bold" v-if="cardata.status != 'sold'"> {{ cardata.price }} </span>
      <span v-if="cardata.status == 'sold'" class="font-weight-bold">n/a</span>
      <br />

      <v-btn
        class="purple darken-3 mt-2 white--text"
        :to="'/details/' + cardata.id"
        v-if="cardata.status != 'sold'"
        >Details</v-btn
      >
    </div>
  </v-card>
</template>

<script>
export default {
  props: {
    cardata: {
      type: Object,
      default: () => {}
    }
  }
};
</script>

<style lang="scss" scoped></style>
