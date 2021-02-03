<template>
  <div id="etext">
    <div class="main">
      <div class="left">
        <input class="input" v-model.lazy="text" type="text" placeholder="Write your text here.exp : Hello World">
        <input class="input" v-model.lazy="key" type="number">
        <button @click="encrypt">Encrypt</button>
      </div>
      <div v-show="encrypted" class="right">
        <h3>Results</h3>
        <hr>
        <p>{{encrypted}}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'etext',
  data(){
    return{
      encrypted : "",
      text : "",
      cLetters : "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split(''),
      sLetters : "abcdefghijklmnopqrstuvwxyz".split(''),
      key: 0
    }
  },
  methods:{
    encrypt(){
      var arr = this.text.split('')
      var k = parseInt(this.key, 10)
      var enT = []
      arr.forEach(l => {
        if(l.match(/^[A-Za-z]+$/)){
          if (l == l.toUpperCase()){
            enT.push(this.cLetters[(this.cLetters.indexOf(l) + k)% this.cLetters.length])
          }
          else{
            enT.push(this.sLetters[(this.sLetters.indexOf(l) + k)% this.sLetters.length])
          }
        }
        else{
          enT.push(l)
        }
      });

      this.encrypted = enT.join('')
      this.text = ""
      this.key = 0
    }

  }
}
</script>

<style>
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
