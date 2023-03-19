<template>
  <NavBar />
  <div class="main">
    <div class="left">
      <h1>Welcome Back</h1>
      <h3>Login to continue</h3>
      <form @submit.prevent="onLogin">
        <div class="login">
          <label for="email">Email</label>
          <input type="email" required id="email" v-model="email" />
        </div>
        <div v-if="error">
          <p class="error">{{ errors.email }}</p>
        </div>
        <div class="login">
          <label for="password">Password</label>
          <input type="password" required id="password" v-model="password" />
        </div>
        <div v-if="errors.password">
          <p class="error">{{ errors.password }}</p>
        </div>
        <button class="button" type="submit">Submit</button>
      </form>
      <p class="signup">
        Don't have an account?
        <router-link to="/signup"> SignUp here</router-link>
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
import { RouterLink } from "vue-router";
import SignupValidations from "@/utils/SignupValidations.js";
// import { useToast } from "vue-toastification";
export default {
  name: "LoginPage",
  components: {
    NavBar,
    RouterLink,
    FooterComponents,
  },
  data() {
    return {
      email: "",
      password: "",
      errors: [],
      user: [],
    };
  },
  methods: {
    onLogin() {
      let validations = new SignupValidations(this.email, this.password);
      // const toast = useToast();
      this.errors = validations.checkValidations();
      if (this.errors.length) {
        return false;
      }

      this.$store.dispatch("auth/login", {
        email: this.email,
        password: this.password,
      });

      // if (
      //   this.email === this.user.email &&
      //   this.password === this.user.password
      // ) {
      //   this.$store.commit("auth/login");

      //   toast.success("Login Successful");
      // } else {
      //   toast.error("Invalid Credentials");
      // }
    },
  },
  created() {
    this.user = JSON.parse(localStorage.getItem("user"));
    console.log(this.user);
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Cedarville+Cursive&family=Poppins:wght@300;400;500;600&family=Roboto:wght@300&family=Source+Sans+Pro:wght@300&display=swap");

* {
  font-family: "Poppins", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.main {
  display: flex;
  flex-direction: row;
  /* justify-content: space-between; */
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
/* form {
  display: flex;
  flex-direction: column;
} */
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
.login{
  display: flex;
  flex-direction: column;
  /* margin-left: 10%;
  margin-right: 10%;
  margin-top: 30px; */
}
.login input {
  /* align-items: center;
  justify-content: center;
  margin: auto; */

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
  /* padding: 15px; */
  margin-right: auto;
  /* margin-left: 50px; */
  margin-bottom: 30px;

  border: 1px solid black;
  cursor: pointer;
  border-radius: 12px;
}
.signup {
  margin-left: 10%;
  font-family: cursive;
  font-size: 20px;
  margin-top: 0%;
  margin-left: auto;
  margin-right: auto;

}
.signup a {
  text-decoration: none;
  color: rgb(42, 106, 45);
}



@media screen and (max-width: 1024px) {
  .main {
    flex-direction: column;
  
  }
  .left {
    width: 80%;
  }

  img {
    display: none;
  }
  .login input {
    width: 100%;
    justify-content: center;
  }
  button {
    width: 100%;
    margin: 0;
  }

  .signup {
    font-size: 25px;
    margin-top: 20px;
  }
}

@media screen and (max-width: 768px) {
  .main {
    flex-direction: column;
  
  }
  .left {
    width: 80%;
  }

  img {
    display: none;
  }
  .login input {
    width: 100%;
    justify-content: center;
  }
  button {
    width: 100%;
    margin: 0;
  }

  .signup {
    font-size: 19px;
    margin-top: 20px;
  }
}
</style>
