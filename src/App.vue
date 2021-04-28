<template>
  <div id="app">
    <PxHeader />
    <router-view />
  </div>
</template>
<script>
import PxHeader from '@/components/PxHeader'
export default {
  components: {
    PxHeader
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Catamaran:wght@800&display=swap');

body {
  background-color: #cdf3ff;
  background-size: 100%;
  background-image: url('./assets/images/fondo.jpg');
  margin: 0;
  font-family: 'Catamaran', sans-serif;
}
</style>
