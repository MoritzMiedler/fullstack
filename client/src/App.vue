<template>
  <v-app>
    <LogoBar></LogoBar>

    <div>
      <router-view :cars="cardata"></router-view>
    </div>
  </v-app>
</template>

<script>
import axios from "axios";
import LogoBar from "@/components/LogoBar.vue";

export default {
  name: "App",
  components: {
    LogoBar
  },
  methods: {
    async getCars() {
      const cars = await axios({ method: "GET", url: "http://127.0.0.1:3000/cars" });

      this.cardata = cars.data;
    }
  },
  created() {
    this.getCars();
  },

  data: () => ({
    cardata: []
  })
};
</script>
