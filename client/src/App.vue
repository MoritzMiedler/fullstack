<template>
  <v-app>
    <LogoBar></LogoBar>
    <v-main>
      <CarCards></CarCards>
    </v-main>
  </v-app>
</template>

<script>
import CarCards from '@/views/CarCards.vue';
import LogoBar from '@/views/LogoBar.vue';
export default {
  name: 'App',
  data: () => ({}),
  components: {
    CarCards,
    LogoBar,
  },
};
</script>
