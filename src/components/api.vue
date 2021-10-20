<template>
 <div class="mrg">
    <!--TODO: Add ramdom API call on backend-->
    <div v-for="quote in quotes" :key="quote.id">
        <p><i>"{{quote.quote}}"</i></p>
        <strong>{{quote.author}}</strong>
    </div>
      <br>
      <div>
        <button class="btn btn-outline-primary" v-on:click="apiCall">Get another quote</button>
      </div>
   </div>
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
    align-items: center;
    text-align: center;
    padding: 30;
  
 }

 .mrg {
   position: absolute;
   left: 50%;
   top: 50%;
   transform: translate(-50%, -50%);
   text-size-adjust: 50%;

}

</style>