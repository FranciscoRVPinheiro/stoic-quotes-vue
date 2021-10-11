<template>
  <div>
    <the-header></the-header>

    <api-call></api-call>
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
  margin: 0;
  background-color: black;
  color: white;
}
</style>