<template>
  <Banner />
  <div class="main-container">
    <h1>Monte o seu hambúrguer</h1>
    <BurgerForm />
  </div>
</template>

<script>

  import Banner from '../components/Banner';
  import BurgerForm from '../components/BurgerForm';

  export default {
    name: 'Home',
    components: {
      Banner,
      BurgerForm,
    }
  }
</script>
