<template>
  <div id="app">
    <nav-tag></nav-tag>
    <div class="action-box" v-show="!enText && !enFile" >
      <h1>What do you like to do ?</h1>
      <button @click="enFile = true">Encrypt File</button>
      <button @click="enText = true">Encrypt Text</button>
    </div>
    <eText v-show="enText"></eText>
    <eFile v-show="enFile"></eFile>
  </div>
</template>
<script>
import nav from "./components/nav";
import etext from "./components/enc-text";
import efile from "./components/enc-file";
export default {
  name: 'App',
  components : {
    "nav-tag": nav,
    eText : etext,
    eFile : efile,
  },
  data(){
    return{
      enText: false,
      enFile: false
    }
  },
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
  text-align: center;
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
