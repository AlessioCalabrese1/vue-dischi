<template>
  <div id="app">
    <Header />
    <Main />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Footer from './components/Footer.vue';
import axios from "axios";


export default {
  name: 'App',
  components: {
    Header,
    Main,
    Footer
}
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
@import "~@fortawesome/fontawesome-free/scss/fontawesome.scss";


</style>
