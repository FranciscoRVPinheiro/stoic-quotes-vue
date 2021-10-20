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
  align-items: center;
  text-align: center;
}

.mrg {
  position: absolute;
   left: 50%;
   top: 50%;
   transform: translate(-50%, -50%);
   padding: 10px;
}
</style>