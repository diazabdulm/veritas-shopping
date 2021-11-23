<template>
  <Header />
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Header,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Oswald");

* {
  box-sizing: border-box;
}

body {
  font-family: "Oswald", sans-serif;
  margin: 0;
  padding: 20px 60px;
  @media screen and (max-width: 800px) {
    padding: 10px;
  }
}

a {
  color: #000;
  text-decoration: none;
}
</style>
