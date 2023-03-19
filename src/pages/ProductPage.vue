<template>
  <NavBar />
  <!-- <RouterLink /> -->
  <div class="main">
   
    <div class="product">
      <!-- <font-awesome-icon icon="fa-solid fa-user-secret" width="30" /> -->
      <div>
        <h1>
          PRODUCTS
          <!-- <span class="user"> {{ user.name }}</span> -->
        </h1>
        <h2 class="text">These are your available products</h2>
      </div>
    </div>


  <div>
    <product-card />
    <!-- <div v-if="loading">
      <p>Loading...</p>
    </div>
    <div v-else>
      <div
        @click="
          () => $router.push({ name: 'product', params: { id: product.id } })
        "
        v-for="product in products"
        :key="product.id"
      >
        <ProductCard :product="product" />
      </div> -->
    </div>
  </div>
      <footer-components />
  <!-- </div> -->

</template>

<script>
import NavBar from "@/components/NavBar.vue";
import FooterComponents from "@/components/FooterComponents.vue";
import ProductCard from '@/components/ProductCard.vue';
// import ProductCard from "@/components/ProductCard.vue";
// import { RouterLink } from "vue-router";
// import { mapState } from "vuex";
// import authenTicatedUser from "../composables/authenTicatedUser";


export default {
  name: "ProductPage",
  components: {
    NavBar,
 
    FooterComponents,
    ProductCard,
    // ProductCard,
    // RouterLink,
  },
  // computed: {
  //   // ...mapState("auth", {
  //   //   user: (state) => state.user.username,
  //   // }),

  //   user() {
  //     return this.$store.getters["auth/user"]
  //   },
  //   ...mapState("products", {
  //     loading: (state) => state.isLoading,
  //     products: (state) => state.products.products,
  //   }),
  // },
  // data() {
  //   return {};
  // },
  // methods: {},
  // mounted() {
  //   this.$store.dispatch("products/getProducts");
  //   console.log(this.$store.getters["auth/user"]);
  // },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cedarville+Cursive&family=Poppins:wght@300;400;500;600&family=Roboto:wght@300&family=Source+Sans+Pro:wght@300&display=swap');
*, *::before, *::after {
  font-family: "Poppins", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.main {
  width: 100%;
  display: grid;
  flex-direction: column;
}
h1{
  font-size: 50px;
  color: rgb(0, 0, 0);
  text-align: center;
  margin-top: 20px;
  font-weight: 500;

}

h2{
  font-size: 30px;
  color: rgb(0, 0, 0);
  text-align: center;
  font-weight: 300;
  margin-top: 20px;
  margin-bottom: 20px;
}

@media screen and (max-width: 1024px) {
h1{
  font-size: 50px;
  text-align: center;
  font-weight: 500;
  
}
h2{
  font-size: 30px;
  text-align: center;
  font-weight: 300;

}
  
}

@media screen and (max-width: 768px) {
h1{
  font-size: 40px;
  text-align: center;
  font-weight: 500;
}
h2{
  font-size: 20px;
  text-align: center;
  font-weight: 300;

}
  
}
</style>
