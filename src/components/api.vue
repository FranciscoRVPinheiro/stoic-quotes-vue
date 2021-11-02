<template>
 <div class="mrg">
    <div class="flexbox" v-for="quote in quotes" :key="quote.id">
        <p><i>"{{quote.quote}}"</i></p>
        <strong>{{quote.author}}</strong>
    </div>
      <br>
      <div class="button-center">
        <button class="btn btn-outline-primary" @click="apiCall">Get another quote</button>
      </div>
   </div>
</template>

<script setup>
import axios from 'axios'
import { ref } from 'vue'

let quotes = ref([])

function apiCall() {
      axios.get('https://stoicism-quotes.herokuapp.com/api/random?format=json')
      .then(response => {
          console.log(response.data)
          quotes.value = response.data
      })
      .catch(error => {
          console.log(error.response)
      })
      }

apiCall(); 
</script>

<style scoped>
 /* .mrg {
   position: absolute;
   left: 50%;
   top: 60%;
   transform: translate(-50%, -50%);
} */

.mrg {
  margin-top: 12rem;
  margin-left: 3rem;
  margin-right: 3rem;
}

/* TODO: Make font-size responsive. Should not clash or bleed into header. */

.flexbox {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  align-items: center;
  /* font-size: 1.5rem; */
  font-size: calc(1em + 1vmin);
}

@media only screen 
  and (-webkit-min-device-pixel-ratio: 2)
  and (orientation: landscape) {
    .flexbox {
      font-size: calc(0.75em + 1vmin);
    }  
    .mrg {
      margin-top: 6rem;
      margin-left: 3rem;
      margin-right: 3rem;
    }
}

.button-center {
    align-items: center;
    text-align: center;
}
</style>