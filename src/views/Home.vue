<template>
  <div id="home">
    <div class="controls">
      <input v-model.lazy="text" type="text" name="text" id="text" placeholder="Enter Your Text here...">
      <input v-model.lazy="key" type="number" name="key" id="key" placeholder="Add your secret Key here..">
      <button>Encrypt</button>
    </div>
    <div v-show="result" class="result">
      <h2>Your Encrypted text</h2>
      <p>{{result}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data(){
    return{
      result: "",
      text: "",
      key: 0
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#home{
  margin: 1em auto;
  padding: 2em;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  .controls{
    display: flex;
    flex-direction: column;
    input{
      background-color: transparent;
      border: none;
      border-bottom: 2px solid $dark-green;
      font-size: 2rem;
      color: $dark-green;
      margin: 1rem auto;
    }
    button{
      width: 50%;
      margin: 1rem auto;
      color: $light-green;
      border: none;
      background-color: $secondary-black;
      font-size: 1.5rem;
      padding: .6em;
      &:hover{
        border: 2px solid $light-green;
        background-color: transparent;
        cursor: pointer;
      }
    }
  }
  .result{
    border: 2px solid $dark-green;
    padding: 1em;
    text-align: center;
    h2{
      color: $dark-green;
      border-bottom: 2px solid $dark-green;
    }
    p{
      color: $blue;
      font-size: 1.3rem;
      margin: .5em;
    }
  }
}
</style>
