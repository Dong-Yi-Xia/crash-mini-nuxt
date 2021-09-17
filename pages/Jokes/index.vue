<template>
  <div>
    <h1>Jokes HomePage</h1>
    <!-- <SearchJokes v-on:search-text="searchText"/>  v-on shorthand @ - eventListener-->
    <SearchJokes @search-text="searchText"/>
    <Joke
      v-for="joke in jokes"
      :key="joke.id"
      :id= "joke.id"
      :joke= "joke.joke"
    />
  </div>
</template>

<script>
import axios from 'axios'
import Joke from '../../components/Joke.vue'
import SearchJokes from '../../components/SearchJokes.vue'

export default {
  components: {
    Joke,
    SearchJokes
  },
  data(){
    return{
      jokes: []
    }
  },
  async created(){
    const config = {
      headers: {
        Accept: 'application/json'
      }
    }
    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config)
      // console.log(res.data.results)
      this.jokes = res.data.results
    } catch (error) {
      console.log(error)
    }
  },
  methods:{
    async searchText(text){
       const config = {
          headers: {
            Accept: 'application/json'
          }
        }
        try {
          const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config)
          // console.log(res.data.results)
          this.jokes = res.data.results
        } catch (error) {
          console.log(error)
        }
      }
  },
  head(){
    return {
      title: 'All Jokes',
      meta: [
        {
          hid: 'description', //unqiue idenfier
          name: 'description', //Acutal meta tag
          content: 'Best corny dad jokes'
        }
      ]
    }
  }
}
</script>

<style>
.joke {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>

