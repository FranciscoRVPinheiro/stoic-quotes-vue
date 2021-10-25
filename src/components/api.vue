<template>
 <div class="mrg">
    <div class="flexbox" v-for="quote in quotes" :key="quote.id">
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
    this.apiCall()
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

<style scoped>
 .mrg {
   position: absolute;
   left: 50%;
   top: 50%;
   transform: translate(-50%, -50%);
}

.flexbox {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  align-items: center;
  font-size: 120%;
}

@media only screen 
  and (-webkit-min-device-pixel-ratio: 2)
  and (orientation: landscape) {
    .flexbox {
      font-size: 90%;
    }  
    .mrg {
      top: 65%;
    }
}
</style>