<template>
  <div class="d-flex justify-content-center bg-dark text-white">
    <div class="text-center"> 
      <div v-if="hasQuotes">

          <!-- Quotes -->
          <div v-for="quote in quotes" :key="quote[id]">
         
          <p class="fst-italic fs-4 text-animation">"{{ quote }}"</p>
          <h3 class="d-flex justify-content-center custom-font text-animation">{{ author }}</h3>
        </div>

          <!-- button -->
        <div class="d-flex justify-content-center p-5 ">
          <button class="btn btn-sample " @click="apiCall">Next</button>
        </div>
 
      </div>
        <div v-else>
          <h1 class="d-flex justify-content-center custom-font text-animation">{{ noConnection }}</h1>
        </div>
    </div>
  </div>


</template>

<script setup>

import axios from 'axios'
import { ref } from 'vue'

let quotes = ref([])
let hasQuotes = ref(false)
let noConnection = ref('')

async function apiCall() {
  try {
      const response = await axios.get('https://stoic-quotes.adaptable.app/quotes/random/quote')
      quotes.value = await response.data
      hasQuotes.value = true
  } catch(error) {
      console.log(error)
      noConnection.value = 'Seems you are not connected to the internet'
  }
}

apiCall()

</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Hurricane&display=swap');

.custom-font {
  font-family: 'Hurricane', cursive;
}


.text-animation {

    -webkit-animation: fadein 3s; /* Safari, Chrome and Opera > 12.1 */
       -moz-animation: fadein 3s; /* Firefox < 16 */
         -o-animation: fadein 3s; /* Opera < 12.1 */
            animation: fadein 3s;
}

@keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Firefox < 16 */
@-moz-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Safari, Chrome and Opera > 12.1 */
@-webkit-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Opera < 12.1 */
@-o-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}


/* custom button */
.btn-sample { 
  color: #ffffff; 
  background-color: #42B883; 
  border-color: #44DB97; 
} 
 
.btn-sample:hover, 
.btn-sample:focus, 
.btn-sample:active, 
.btn-sample.active, 
.open .dropdown-toggle.btn-sample { 
  color: #ffffff; 
  background-color: #4CE6B8; 
  border-color: #44DB97; 
} 
 
.btn-sample:active, 
.btn-sample.active, 
.open .dropdown-toggle.btn-sample { 
  background-image: none; 
} 
 
.btn-sample.disabled, 
.btn-sample[disabled], 
fieldset[disabled] .btn-sample, 
.btn-sample.disabled:hover, 
.btn-sample[disabled]:hover, 
fieldset[disabled] .btn-sample:hover, 
.btn-sample.disabled:focus, 
.btn-sample[disabled]:focus, 
fieldset[disabled] .btn-sample:focus, 
.btn-sample.disabled:active, 
.btn-sample[disabled]:active, 
fieldset[disabled] .btn-sample:active, 
.btn-sample.disabled.active, 
.btn-sample[disabled].active, 
fieldset[disabled] .btn-sample.active { 
  background-color: #42B883; 
  border-color: #44DB97; 
} 
 
.btn-sample .badge { 
  color: #42B883; 
  background-color: #ffffff; 
}

</style>
