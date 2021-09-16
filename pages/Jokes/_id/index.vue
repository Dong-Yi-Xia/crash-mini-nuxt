<template>
  <!-- having localhost:3000/jokes/id need to create a folder inside parent folder with a underscore in front, _id, with every nested route /../../ you need a _folder -->
  <div>
      <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
      <h2>{{joke}}</h2>
      <hr>
      <small>Joke ID:  {{$route.params.id}}</small>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return{
      joke: {}
    }
  },
  async created(){
    const config = {
      headers: {
        Accept: 'application/json'
      }
    }
    try {
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config)
      // console.log(res.data.joke)
      this.joke = res.data.joke
    } catch (error) {
      console.log(error)
    }
  },
  head() { //the head section on the html
    return {
      title: this.joke,
      meta: [
        {
          hid: 'description', //unqiue idenfier
          name: 'description', //Acutal meta tag
          content: 'Single Best corny dad jokes HP'
        }
      ]
    }
  },
}
</script>

<style>

</style>
