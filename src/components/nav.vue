<template>
  <div id="nav">
    <ul>
      <li> <a class="nav-link" href="/">R()tEn</a></li>
    </ul>
    <ul>
      <li> <a class="nav-link" href="/">Home</a></li>
      <li> <a class="nav-link" href="#">About</a></li>
    </ul>
  </div>
</template>

<script >

export default {
  name: 'App',
}
</script>

<style scoped>
#nav {
  font-family:'Rock Salt', cursive;
  background-color: rgb(199, 100, 64);
  width: 50%;
  height: 2%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  border-radius: 0rem 3rem .2rem;
  box-shadow: 3px 2px 10px 1px grey;
}
ul{
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  list-style: none;
}
ul li{
  margin: 1rem;
}
.nav-link{
  color: snow;
  text-decoration: none;
  font-size: 1.4rem;
}

.nav-link:hover{
  cursor: pointer;
  color: rgba(255, 250, 250, 0.637);
  font-weight: bolder;
}


</style>
