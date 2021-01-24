<template>
  <div id="nav">
    <ul>
      <li><router-link v-bind:to="'/'">Home</router-link></li>
      <li><router-link v-bind:to="'/about'">About</router-link></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "nav-bar"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#nav{
  width: 50%;
  margin: 0 auto;
  background-color: $secondary-black;
  padding: .3em;
  box-shadow: $shadow;
  ul{
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    list-style: none;
    li{
      a{
        text-decoration: none;
        color: $dark-green;
        font-size: 1.6rem;
        &:hover{
          color: $light-green;
        }
      }
    }

  }
}
</style>
