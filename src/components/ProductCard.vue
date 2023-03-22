<template>
  <div class="main">
    <div class="cards" v-for="product in products" :key="product.id">
       <div>
      <img :src="product.images[0]" alt="" />
   </div>
        <div>
          <h1 class="tittle" >
            {{ product.title }}
          </h1>
          <font-awesome-icon icon="fa-solid fa-bookmark" />
        </div>
        <div>
          <p class="description">
            {{ product.description }}
          </p>
        </div>
        <!-- reviews -->
        <div>
          <font-awesome-icon icon="fa-solid fa-star" />
          <p class="rating">
            {{ product.rating }}
            <span>(1112 Reviews)</span>
          </p>
        </div>
        <!-- price and Category -->
     
      <div >
        <p class="price">$ {{ product.price }}</p>
        <p>{{ product.category }}</p>
      </div>
     <div class="more">
        <button class="more">
          <router-link :to="{ name: 'product', params: { id: product.id } }">
            View Product
          </router-link>
        </button>
     </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "ProductCard",
  data() {
    return {
      products: [],
    };
  },
  async created() {
    try {
      const response = await axios.get("https://dummyjson.com/products");
      this.products = response.data.products.slice(0, 12);
      console.log(this.products);
    } catch (error) {
      console.log(error);
    }
  },
  // name: "ProductCard",
  // props: {
  //   product: {
  //     type: Object,
  //     required: true,
  //   },
  // },
  // data() {
  //   return {};
  // },
  // methods: {},
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
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2.5rem;

}
.cards {
  max-width: 450px;
  margin: 10px;
  border: 1px solid rgb(190, 188, 188);
  border-radius: 5px;
  box-shadow: 0 0 10px #ccc;
  display: grid;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
}
img {
  width: 100%;
  height: 170px;
  object-fit: cover;
}
.tittle {
  justify-content: space-between;
  align-items: center;
  width: 100%;
}
 h1 {
  font-size: 20px;
  font-weight: 500;
  color: rgb(0, 0, 0);

}
.description {
  font-size: 15px;
  font-weight: 300;
  color: rgb(0, 0, 0);
}
.rating {
  align-items: center;
  font-size: 15px;
  font-weight: 300;
  color: rgb(152, 41, 41);
}
.rating span {
  font-size: 12px;
  font-weight: 300;
  color: rgb(152, 41, 41);
}
.price {
  justify-content: space-between;
  align-items: center;
  width: 100%;
}
.price p {
  font-size: 15px;
  font-weight: 300;
  color: rgb(0, 0, 0);
}
.more {
  width: 100%;

  justify-content: center;
}
.more button {
  width: 100%;
  height: 40px;
  background-color: #2a6a2d;
  color: white;
  border-radius: 5px;
  border: none;
  cursor: pointer;
}
.more button a {
  text-decoration: none;
  color: white;
}


@media screen and (max-width: 1024px) {
  .main {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2.5rem;
  }
  
}


@media screen and (max-width: 768px) {
  .main {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 2.5rem;

  }
  
}
</style>
