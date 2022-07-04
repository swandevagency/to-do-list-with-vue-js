<template>
  <div class="container">
    <div>
      <h1>To-Do-List</h1>
    </div>
    <hr />
    <Main />
  </div>
</template>

<script>
import Main from './Main.vue';
// import Footer from './Footer.vue';
export default {
  components: {
    Main,
    // Footer,
  },
};
</script>

<style scoped>
h1 {
  color: rgb(68, 68, 68);
  margin: 20px 0;
}
.container {
  width: 50%;
  text-align: center;
  margin: 100px auto;
  border: 1px solid rgb(211, 211, 211);
  border-radius: 16px;
  background-color: rgb(241, 241, 241);
  box-shadow: 0 0 18px rgba(0, 0, 0, 0.2);
}
</style>
