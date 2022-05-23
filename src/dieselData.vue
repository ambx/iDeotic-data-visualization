<template>
  <dieselBangalore />
  <br />
  <dieselAllahabad />

</template>

<script>
import dieselBangalore from './components/dieselBangalore.vue';
import dieselAllahabad from './components/dieselAllahabad.vue'

export default {
  name: 'diesel',
  components: {
    'dieselBangalore': dieselBangalore,
    'dieselAllahabad':dieselAllahabad
  }
}

</script>

<style>
@import "./assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}
</style>
