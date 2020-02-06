
<style scoped>
  h1 {
    margin: 40px 0 0;
  } 
</style>

<template>
  <div class="hello">
    <h1>{{ msg }}</h1> 
  </div>
</template>

<script>
  export default {
    name: 'IntroContent',
    props: {
      msg: String
    }
  }
</script>