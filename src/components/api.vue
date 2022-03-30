<template>
  <div class="d-flex justify-content-center bg-dark text-white">
    <div class="text-center"> 
      <div v-if="hasQuotes">

          <!-- Quotes -->
        <div v-for="quote in quotes" :key="quote.id">
          <p class="fst-italic fs-4">"{{ quote.quote }}"</p>
          <h3 class="d-flex justify-content-center custom-font"><strong>{{ quote.author }}</strong></h3>
        </div>

          <!-- button -->
        <div class="d-flex justify-content-center p-5">
          <button class="btn btn-lg btn-primary" @click="apiCall">Next</button>
        </div>
 
      </div>
    </div>
  </div>


</template>

<script setup>

import axios from 'axios'
import { ref } from 'vue'

let quotes = ref([])
let hasQuotes = ref(false)

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