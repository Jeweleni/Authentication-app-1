<template>

  <RouterView />
  <RouterLink />


   
</template>

<script>
import { RouterView } from "vue-router";
import { RouterLink } from "vue-router";

export default {
  name: "App",
  components: {
    RouterView,
    RouterLink,
  },
  mounted() {
    this.$store.getters("auth/intializeState");
  },
};
</script>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Cedarville+Cursive&family=Poppins:wght@300;400;500;600&family=Roboto:wght@300&family=Source+Sans+Pro:wght@300&display=swap');


#app {
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;

}

</style>
