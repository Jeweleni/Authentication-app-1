<template>
  <NavBar />
  <!-- <div>
    <div>
      <img :src="product.thumbnail" alt="product" />
      <div>
        <h1>
          {{ product.title }}
        </h1>

        <p>
          <span>
            <font-awesome-icon icon="fa-solid fa-star" />
          </span>
          {{ product.rating }}
        </p>
        <div>
          <h2>Description:</h2>
          <p>{{ product.description }}</p>
        </div>
        <div>
          <h2>Category:</h2>
          <p>
            {{ product.category }}
          </p>
        </div>
        <div>
          <h2>Price:</h2>
          <p>${{ product.price }}</p>
        </div>
        <div>
          <router-link
            :to="{
              name: 'product-images',
              // params: { id: product.id },
            }"
          >
            <h2>Show Other Images</h2>
          </router-link>
          <hr />
        </div>
      </div>
    </div>
  </div> -->
  <div class="main">
    <div class="left">
      <img :src="img" />
    </div>
    <div class="right">
  
       <h2>{{ category }}</h2>
        <h1>{{ brand }}</h1>
       

        <h1>{{ title }}</h1>
        
        <h2>{{ price }}</h2>
  

        <h1>{{ rating }}</h1>

     
        <h1>{{ description }}</h1>
  
      <div class="goBack"  @click="goBack">
   Go Back
      </div>
  
    </div>
  
  </div>
    <footer-components />
</template>

<script>
import NavBar from "@/components/NavBar.vue";
// import { useRoute } from "vue-router";
import axios from "axios";
import FooterComponents from '@/components/FooterComponents.vue';
export default {
  name: "ProductDetails",
  components: {
    NavBar,
    FooterComponents,
  },

created() {
    this.getProducts();
  },
  data() {
    return {
      products: [],
      img: "",
      brand: "",
      category: "",
      title: "",
      price: "",
      rating: "",
      description: "",
    };
  },
  methods: {
    async getProducts() {
      try {
        const parameter = this.$route.params.id;
        console.log(parameter)
        const res = await axios.get(
          `https://dummyjson.com/products/${parameter}`
        );
        console.log(res.data);
        this.products = res.data;
        this.img = res.data.images[0];
        this.brand = res.data.brand;
        this.category = res.data.category;
        this.title = res.data.title;
        this.price = `$ ${res.data.price}`;
        this.rating = `Rating: ${res.data.rating}`;
        this.description = res.data.description;
      } catch (err) {
        console.log(err);
      }
    },
    goBack() {
      this.$router.push("/products");
    },
  },

  // data() {
  //   return {
  //     product: {},
  //   };
  // },
  // methods: {
  //   fetchProduct() {
  //     const route = useRoute();
  //     const { id } = route.params;
  //     const endpoint = `https://dummyjson.com/products/${id}`;
  //     axios
  //       .get(endpoint)
  //       .then((res) => {
  //         this.product = res.data;
  //       })
  //       .catch((err) => {
  //         console.log(err);
  //       });
  //   },
  // },
  // mounted() {
  //   console.log(this.$route.params.id);
  //   this.fetchProduct();
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
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  background-color: #f5f5f5;
}
.left {
  width: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.right {
  width: 50%;
  font-size: 14px;
  line-height: 180%;
  display: flex;
  font-weight: 300;
  flex-direction: column;
  /* justify-content: space-between; */
  /* border: 1px solid rgb(241, 3, 3); */
  gap: 16px;
}
h1 {

  font-size: 15;

}
h2{
  font-size: 15;
}

.rating {
  font-size: 15px;
  font-weight: 300;
  color: #666;
}
.description {
font-size: 15px;
  font-weight: 300;
  margin-top: 50px;
  margin-bottom: 10px;
  color: rgb(0, 0, 0);
}
.goBack{
  width: 100%;
  background-color: #000;
  color: #fff;
  cursor: pointer;
}



@media screen and (max-width: 1024px) {
  .main {
    flex-direction: column;
    height: 100%;
  }

  img {
    width: 100%;
    height: 100%;
    margin-top: 20px;
  }
  h1{
    font-size: 20px;
    margin: 0%;
  }
}

@media  screen and (max-width: 768px) {
  .main {
    flex-direction: column;

  }

  img {
    max-width: 100%;
    height: auto;
    margin-top: 20px;
  }
  .right{
    width: 100%;
    padding: 20px;
    font-size: 12px;
  }
}

</style>