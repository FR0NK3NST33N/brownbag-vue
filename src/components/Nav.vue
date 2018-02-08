<template>
  <div>
    <router-link to="/"><button>Go to Home</button></router-link>
    <router-link to="/test"><button>Go to Test</button></router-link>
    <br />
    <br />
  </div>
</template>

<script>
export default {
  name: 'Nav',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  float: left;
}
</style>
