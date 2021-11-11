<template>
  <PasswordGenerator titleOfPage="PASSWORD GENERATOR" />
</template>

<script>
import PasswordGenerator from "./components/PasswordGenerator.vue";

export default {
  name: "App",
  components: {
    PasswordGenerator,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Arvo:wght@400;700&display=swap");

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: auto;
}
html {
  font-family: "Arvo", serif;
}
body {
  text-align: center;
  background-color: #0f0a0a;
}
</style>
