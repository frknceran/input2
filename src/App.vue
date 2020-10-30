<template>
  <div id="app">
      <Name></Name>
  </div>
</template>

<script>
import Name from "./components/Name"

export default {
  name: 'App',
  components: {
    Name
  }
}
</script>

<style scoped>
#app {
  text-align: center;
  width: 600px;
  color: #2c3e50;
  margin: 0 auto;
}
</style>
