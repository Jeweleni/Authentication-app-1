<template>
  <div class="home">
    <NavBar />
    <div class="main">
      <h2 class="text">
        Show the world <br />
        the digital you
      </h2>
      <button>
        <router-link to="/login" class="button"> View Products </router-link>
      </button>
     
    </div>

  </div>
   <footer-components />
</template>

<script>
import NavBar from "../components/NavBar.vue";
import { RouterLink } from "vue-router";
import FooterComponents from '@/components/FooterComponents.vue';
export default {
  name: "HomePage",
  components: {
    NavBar,
    RouterLink,
    FooterComponents,
  },
};
</script>

<style scoped>

  @import url('https://fonts.googleapis.com/css2?family=Cedarville+Cursive&family=Poppins:wght@300;400;500;600&family=Roboto:wght@300&family=Source+Sans+Pro:wght@300&display=swap');

.home {
  font-family: "Poppins", sans-serif;
  margin-top: 0%;
  background: url("../assets/homebackground.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  object-fit: contain;
  max-width: 100%;
  width: 100%;
  height: 100vh;
}

.main {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-top: 0%;
  gap: 10px;
}

.main button {
  width: 200px;
  height: 50px;
  margin-left: 140px;
  background-color: rgb(42, 106, 45);
  color: white;
  border-radius: 10px;
  border: none;
}

.main button a {
  text-decoration: none;
  color: white;
}

.text {
  color: rgb(0, 0, 0);
  font-size: 70px;
  text-align: left;
  padding-top: 110px;
  padding-left: 140px;
  font-family: "Roboto", sans-serif;
}
.footer {
  color: rgb(0, 0, 0);
  font-size: 20px;
  text-align: left;
  padding-top: 150px;
  font-family: "Roboto", sans-serif;
}
@media screen and (max-width: 768px) {
  .home {
    background: url("../assets/homebackground.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    width: 100%;
    height: 100vh;
  }
  .main {
    display: flex;
    flex-direction: column;
    margin-left: -30px;
    margin-top: -100px;
    gap: 10px;
  }
  .text {
    color: rgb(0, 0, 0);
    font-size: 50px !important;
    padding-top: 200px;
    padding-left: 120px;
    margin: 0%;
  }
  button {
    width: 200px;
    height: 50px;
    margin-left: 120px;
    background-color: rgb(42, 106, 45);
    color: white;
    border-radius: 10px;
    border: none;
  }
  .footer {
    display: flex;
    flex-direction: column;
    margin-left: 2px;
    margin-top: -240px;
    gap: 10px;
    padding-top: 200px;
    padding-left: 50px;
    font-size: 10px;
    font-family: "Roboto", sans-serif;
  }
}

@media screen and (max-width: 1024px) {
  .home {
    /* background: url("../assets/homebackground.jpg"); */
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    max-width: 100%;
    width: 100%;
    height: 100vh;
  }
  .text {
    font-size: 75px;
    padding-top: 250px;
    padding-left: 120px;
    font-family: "Roboto", sans-serif;
  }
  .main button {
    width: 200px;
    height: 50px;
    margin-left: 120px;
    background-color: rgb(42, 106, 45);
    color: white;
    border-radius: 10px;
    border: none;
  }
  .footer {
    padding-top: 330px;
  }
}
</style>
