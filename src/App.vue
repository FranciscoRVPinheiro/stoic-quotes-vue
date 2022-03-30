<template>

  <div class="container-fluid m-0 p-0">
    <TheHeader />
  </div>

  <div class="spacing-top">
    <Api />
  </div>

</template>

<script setup>
import TheHeader from './components/TheHeader.vue';
import Api from './components/api.vue';
</script>

<style>
.spacing-top {
  margin: 100px 30px;

}
</style>