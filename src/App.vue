<template>
  <Navbar :logo="logo_src" :alt="app_name"/>
  <router-view/>
  <Footer />
</template>

<script>
  import Navbar from './components/Navbar';
  import Footer from './components/Footer';

  export default {
    name: 'App',
    components: {
      Navbar,
      Footer,
    },
    data() {
      return {
        logo_src: '/img/logo.png',
        app_name: 'Make Your Burger',
      }
    }
  }
</script>

<style>

  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400&display=swap');

  * {
    box-sizing: border-box;
    font-family: 'Roboto', Helvetica, sans-serif;
    margin: 0;
    padding: 0;
  }

  .main-container {
    margin: 50px;
    min-height: 250px;
  }

  h1 {
    color: #222;
    font-size: 42px;
    margin-bottom: 30px;
    text-align: center;
  }
</style>
