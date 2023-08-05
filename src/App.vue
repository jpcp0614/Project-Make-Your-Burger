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

</style>
