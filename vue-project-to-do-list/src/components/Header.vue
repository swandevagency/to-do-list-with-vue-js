<template>
<div class="container">
  <div>
    <h1>To-Do-List</h1>
  </div>
  <Main />
  <Footer />
</div>
</template>

<script>
  import Main from './Main.vue'
  import Footer from './Footer.vue'
  export default {
    // name: Header,
    components: {
      Main,
      Footer
    }
  }
</script>

<style scoped>
  h1 {
    color: rgb(68, 68, 68);
  }
  .container {
    text-align: center;
    margin: 100px 200px;
    border: 1px solid rgb(182, 182, 182);
  }
</style>