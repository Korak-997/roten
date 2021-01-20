<template>
  <div id="app">
    <nav-tag></nav-tag>
    <div class="main">
      <div class="left">
        <input class="input" v-model.lazy="input" type="text" placeholder="Write your text here.exp : Hello World">
        <input class="input" v-model.lazy="key" type="number">
        <button @click.prevent="encrypt">Encrypt</button>
      </div>
      <div v-show="encrypted" class="right">
      </div>
    </div>
  </div>
</template>
<script>
import nav from "./components/nav";
export default {
  name: 'App',
  components : {
    "nav-tag": nav
  },
  data(){
    return{
      encrypted : "",
      text : "",
      key: 0
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rock+Salt&display=swap');
*{
  margin: 0;
  padding: 0%;
  box-sizing: border-box;
}
body{
  background-color: rgba(0, 0, 0, 0.753);
  width: 100vw;
  height: 100vh;
}
#app{
}
.main{
  margin: 2rem auto;
  border: 2px solid rgb(199, 100, 64);
  width: 90%;
  height: 80%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  padding: 2rem;
}
.left{
  width: 30%;
  display: flex;
  flex-direction: column;
}

.right{
  box-shadow: 3px 2px 10px 1px grey;
  padding: 1rem;
  color: snow;
}

.input{
  text-align: center;
  background-color: transparent;
  color: snow;
  padding: 1rem;
  border: none;
  border-bottom: 2px solid rgb(199, 100, 64);
  margin-bottom: 2rem;
}

.main button{
  background-color: rgb(199, 100, 64);
  border: none;
  border-radius: 2rem 1rem;
  color: snow;
  padding: 1rem;
  font-size: 1.5rem;
}

.main button:hover{
  background-color: transparent;
  cursor: pointer;
  border: 2px solid rgb(199, 100, 64) ;
}
</style>
