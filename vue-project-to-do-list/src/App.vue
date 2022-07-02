<template>
  <Header />
</template>

<script>
import Header from './components/Header.vue';

export default {
  data() {
    return {

    };
  },
  components: {
    Header,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap');
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Open Sans', sans-serif;
}
</style>
