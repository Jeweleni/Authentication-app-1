<template>
  <NavBar />
  <div class="main">
    <div class="left">
      <h1>WELCOME!!!</h1>
      <h3>Sign up to create your account</h3>
      <form @submit.prevent="onRegister()">
        <div class="signup">
          <label for="name">Username</label>
          <input type="name" required id="name" v-model="username" />
        </div>
        <div v-if="errors.username">
          <p class="error">{{ errors.username }}</p>
        </div>
        <div class="signup">
          <label for="email">Email</label>
          <input type="email" required id="email" v-model="email" />
        </div>
        <div v-if="errors.email">
          <p class="error">{{ errors.email }}</p>
        </div>
        <div class="signup">
          <label for="password">Password</label>
          <input type="password" required id="password" v-model="password" />
        </div>
        <div v-if="errors.password">
          <p class="error">{{ errors.password }}</p>
        </div>

        <button type="submit">Submit</button>
      </form>
      <p class="login">
        Already have an account?
        <router-link to="/login">Login here</router-link>
      </p>
    </div>

    <div class="right">
      <img src="../assets/login.jpeg" />
    </div>
  </div>
  <footer-components />
</template>

<script>
import FooterComponents from "@/components/FooterComponents.vue";
import NavBar from "@/components/NavBar.vue";
import { mapActions } from "vuex";
import { RouterLink } from "vue-router";
import SignupValidations from "../utils/SignupValidations";
import { useToast } from "vue-toastification";

export default {
  name: "SignUp",
  components: {
    NavBar,
    RouterLink,
    FooterComponents,
  },
  data() {
    return {
      username: "",
      email: "",
      password: "",
      errors: [],
    };
  },

  methods: {
    ...mapActions({
      // register: "auth/signup",
    }),
    onRegister() {
      const toast = useToast();
      let validations = new SignupValidations(
        this.email,
        this.password,
        this.username
      );
      this.errors = validations.checkValidations();
      if (this.errors.length) {
        return false;
      }
      this.$store.dispatch("auth/signup", {
        email: this.email,
        password: this.password,
        username: this.username,
      });
      toast.success("You have successfully signed up");
      this.$router.push("/login");
    },
  },
  mounted() {
    this.$store.commit("auth/clearUser");
  },
};
</script>

<style scoped>

@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap");

* {
  font-family: "Poppins", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-top: 0%;
  gap: 10px;
  height: 100vh;
}

.left {
  width: 50%;
  max-width: 500px;
  /* border: 1px solid rgb(125, 0, 0); */
  display: flex;
  flex-direction: column;
  margin: auto;
}

.right {
  width: 50%;
}

img {
  width: 100%;
  height: 100vh;
  border-radius: 6rem 0 0 2rem;
}

h1 {
  text-align: center;
  margin-top: 50px;
  color: rgb(42, 106, 45);
}

form {
  display: flex;
  flex-direction: column;
}

h3 {
  text-align: center;
  margin-top: 20px;
  margin-bottom: 20px;
  color: rgb(12, 24, 13);
}

/* label {
  font-size: 20px;
  margin-left: 10%;
} */

.signup{
  display: flex;
  flex-direction: column;
  /* margin-left: 10%;
  margin-right: 10%;
  margin-top: 30px; */
}

.signup input {
  /* align-items: center;
  justify-content: center; */
  /* margin: auto; */

  padding: 1rem;
  border: 1px solid black;
  /* margin-right: auto;
  margin-left: auto; */
  display: flex;
  margin-bottom: 30px;
  border-radius: 12px;
}

button {
  width: 500px;
  height: 40px;
  /* padding-left: 20px; */
  margin-right: auto;
  /* margin-left: 10px; */
  margin-bottom: 30px;
  border: 1px solid black;
  cursor: pointer;
  border-radius: 12px;
}
.login {
  margin-left: 10%;
  font-family: cursive;
  font-size: 20px;
  margin-top: 0%;
  /* margin-left: auto;
  margin-right: auto; */
}

.login a {
  text-decoration: none;
  color: rgb(42, 106, 45);
}

@media screen and (max-width: 768px) {
  .main {
    flex-direction: column;
  }
  .left {
    width: 100%;
  }

  img {
    display: none;
  }
  .signup input {
    width: 80%;
  }
  button {
    width: 80%;
  }
}

@media screen and (max-width: 1024px) {
  .main {
    flex-direction: column;
    margin: 0 auto;
    align-items: center;
  }
  .left {
    width: 100%;
  }

  img {
    display: none;
  }
  .signup input {
    /* width: 80%; */

  align-items: center;
  justify-content: center;
  margin: auto;

  padding: 1rem;
  border: 1px solid black;
  /* margin-right: auto;
  margin-left: auto; */
  display: flex;
  margin-bottom: 30px;
  border-radius: 12px;

  }
  button {
    width: 80%;
    margin-left: 50px;
  }
}
</style>
