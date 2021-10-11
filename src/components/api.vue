<template>
  <div>
      <h3>{{quote.quote}}</h3>
      <p>{{quote.author}}</p>
      <button v-on:click="reloadPage">Get another quote</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
        quote: []
    };
  },
  created(){
      axios.get('https://stoicism-quotes.herokuapp.com/api/?format=json')
      .then(response => {
          //console.log(response.data)
          this.quote = response.data
      })
      .catch(error => {
          console.log(error.response)
      })
  },
  methods: {
      reloadPage() {
      window.location.reload();
    }
  }
};
</script>

<style>
 div {
    color: white;
    align-items: center;
    text-align: center;
 }
</style>