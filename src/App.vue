<template>
  <dieselData />
</template>

<script>
import dieselData from './dieselData.vue'

export default {
  name: 'app',
  components: {
    'dieselData': dieselData
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
