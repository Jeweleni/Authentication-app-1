<template>
  <div>
    <p class="footer">All rights reserved. © EMJCREATES_ 2023</p>
  </div>
</template>

<script>
export default {
  name: "FooterComponents",
};
</script>

<style scoped>
.footer {
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: right;
  margin: 0%;
  font-size: 20px;
  color: rgb(255, 255, 255);
  background-color: rgb(0, 0, 0);

}

@media screen and (max-width: 768px) {
    .footer{
        font-size: 10px;
        padding: 1rem;
    }
}
</style>