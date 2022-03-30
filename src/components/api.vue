<template>
  <div class="d-flex justify-content-center">
    <div class="text-center"> 
      <div v-if="hasQuotes">
        <div v-for="quote in quotes" :key="quote.id">
          <p><em>"{{ quote.quote }}"</em></p>
          <h3 class="d-flex justify-content-center custom-font"><strong>{{ quote.author }}</strong></h3>
        </div>

        <div class="d-flex justify-content-center p-3">
          <button class="btn btn-outline-primary" @click="apiCall">Next quote</button>
        </div>
      </div>

      <div v-else> 
          <p><em>Patience is a virtue</em></p>
      </div>
    </div>
  </div>

</template>

<script setup>

import axios from 'axios'
import { ref } from 'vue'

let quotes = ref([])
let hasQuotes = ref(false)

// function apiCall() {
//       axios.get('https://stoicism-quotes.herokuapp.com/api/random?format=json')
//       .then(response => {
//           quotes.value = response.data
//       })
//       .catch(error => {
//           console.log(error.response)
//       })
// }

async function apiCall() {
  try {
      const response = await axios.get('https://stoicism-quotes.herokuapp.com/api/random?format=json')
      quotes.value = await response.data
      hasQuotes.value = true
  } catch(error) {
      console.log(error)
  }
}

apiCall()

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Hurricane&display=swap');

.custom-font {
  font-family: 'Hurricane', cursive;
}


</style>