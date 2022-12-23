<template>
  <div class="hello">
    <h1>Joke App</h1>
    <button @click="showJoke()">Show Joke</button>
    <div v-if="joke">
      <p>{{ joke }}</p>
  </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      joke:''
    }
  },
  methods: {
   async showJoke() {
      let config = {
        headers: {
          'accept': 'application/json'
        }
      }
      const joke = await axios.get('https://icanhazdadjoke.com', config);
      this.joke = joke.data.joke
    }
  }
}
</script>
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
