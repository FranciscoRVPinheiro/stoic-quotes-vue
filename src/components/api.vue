<template>

  <!--TODO: Add ramdom API call on backend-->
  <div v-for="quote in quotes" :key="quote.id">
      <h3>{{quote.quote}}</h3>
      <p>{{quote.author}}</p>
  </div>
  <button v-on:click="apiCall">Get another quote</button>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
        quotes: [] 
    };
  },
  created(){
      axios.get('https://stoicism-quotes.herokuapp.com/api/random?format=json')
      .then(response => {
          console.log(response.data)
          this.quotes = response.data
      })
      .catch(error => {
          console.log(error.response)
      })
  },
  methods: {
      reloadPage() {
      window.location.reload();
      },
      apiCall() {
        axios.get('https://stoicism-quotes.herokuapp.com/api/random?format=json')
      .then(response => {
          console.log(response.data)
          this.quotes = response.data
      })
      .catch(error => {
          console.log(error.response)
      })

      }
  }
};
</script>

<style>
 div {
    color: white;
    align-items: center;
    text-align: center;
    padding: 30;

 }

</style>