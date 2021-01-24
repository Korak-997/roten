<template>
  <nav-bar></nav-bar>
  <router-view />
</template>

<script>
import Navbar from "./components/nav"
export default {
  name: "App",
  components:{
    "nav-bar": Navbar
  }
};
</script>

<style lang="scss">
#app {
}

</style>
