<template>
  <div>
    <TheHeader />
      <div>
        <Api />
      </div>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import Api from './components/api.vue';


export default {
  components: {
    TheHeader,
    Api,
  },
};
</script>

<style>

</style>