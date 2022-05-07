<template>
 <div>
<h1>Joke App</h1>
<button @click="showJoke()">Show Joke</button>
<div v-if="joke">
<p>{{joke}}</p>
</div>
 </div>
</template>

<script>
import axios from 'axios';



export default {
  data(){
    return{ 
      joke:''
    }
  },
  methods:{
    async showJoke(){
      let config ={
        headers: {
          'Accept': 'application/json'
        }
      }
      const joke = await axios.get('https://icanhazdadjoke.com', config);
      this.joke = joke.data.joke
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
