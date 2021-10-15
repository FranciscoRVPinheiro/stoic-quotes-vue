<template>
  <div>
    <the-header></the-header>
    <div class="mrg">
      <api-call></api-call>
    </div>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import api from './components/api.vue';

export default {
  components: {
    'the-header': TheHeader,
    'api-call': api,
  },
  data() {
    return {
    };
  },
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  background-color: black;
  color: white;
  margin: 0; 
}

.mrg {
   margin: 25px;
}
</style>