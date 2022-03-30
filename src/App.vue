<template>
  <div class="container-fluid bg-dark new-class">
    <div class="m-0 p-0">
      <TheHeader />
    </div>

    <div class="spacing-top">
      <Api />
    </div>
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

.new-class {
  min-height: 100vh;
}

</style>