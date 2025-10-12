<script setup>
import MsButton from './components/ms-button/MsButton.vue';
import Counter from './views/Counter.vue'
</script>

<template>
  <ms-button type="primary" icon="fa-car">Car Button</ms-button>

  <br>
  <br>

  <ms-button type="warning" icon="fa-refresh" position-icon="right">Refesh Button</ms-button>

  <br>
  <br>
  <hr />
  <Counter msg="Counter" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
