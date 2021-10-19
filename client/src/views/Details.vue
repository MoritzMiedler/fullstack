<template>
  <div class="d-flex justify-center">
    <v-card class="ma-5 d-flex flex-column justify-end " style="width:500px">
      <v-img :src="filterCar.image"></v-img>
      <div class="text-h4 my-2 d-flex justify-center">
        {{ filterCar.title }} <span v-if="filterCar.status == 'sold'">*RESERVED*</span>
      </div>
      <v-simple-table>
        <thead>
          <tr>
            <th>Price</th>
            <th>Miles</th>
            <th>Year of Make</th>
            <th>Current Owner</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>{{ filterCar.price }}</td>
            <td>{{ filterCar.miles }}</td>
            <td>{{ filterCar.year_of_make }}</td>
            <td>{{ filterCar.owner }}</td>
          </tr>
        </tbody>
      </v-simple-table>
      <p class="mx-5">{{ filterCar.description }}</p>
      <div class="d-flex mx-5 mb-3">
        <v-btn class=" purple darken 2 white--text" to="/">Go back</v-btn>
        <v-spacer></v-spacer>
        <v-btn class=" green darken 2 white--text" @click="deleteCar">Delete</v-btn>
        <v-spacer></v-spacer>
        <v-btn class=" red darken 2 white--text" @click="buyCar" v-if="filterCar.status != 'sold'"
          >Order</v-btn
        >
      </div>
    </v-card>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {};
  },
  props: {
    id: {
      type: String
    },
    cars: {
      type: Array
    }
  },

  computed: {
    filterCar() {
      return this.cars.find(el => el.id == this.id);
    }
  },
  methods: {
    async buyCar(event) {
      event.title += " RESERVED!";
      await axios({
        method: "PATCH",
        url: `http://127.0.0.1:3000/cars/${this.id}`,
        "content-type": "application/json",
        data: { status: "sold" }
      });
      this.$router.go();
    },
    async deleteCar() {
      await axios({
        method: "DELETE",
        url: `http://127.0.0.1:3000/cars/${this.id}`
      });
      this.$router.go();
    }
  }
};
</script>

<style lang="css" scoped></style>
