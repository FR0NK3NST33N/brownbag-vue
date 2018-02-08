<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <router-link to="/">Go to Home</router-link>
  </div>
</template>

<script>
export default {
  name: 'Test',
  data () {
    return {
      msg: 'Welcome to the Test Page of Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-weight: normal;
}
</style>
