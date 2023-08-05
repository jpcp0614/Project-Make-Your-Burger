<template>
  <div id="main-banner">
    <h1 class="line">Make Your Burger</h1>
  </div>
</template>

<script>
  export default {
    name: 'Banner',
  }
</script>

<style scoped>
  #main-banner {
    align-items: center;
    background-image: url('/public/img/burger.jpg');
    background-position: 0 -250px;
    background-size: cover;
    display: flex;
    height: 500px;
    justify-content: flex-start;
  }

  #main-banner h1 {
    color: #fff;
    font-size: 60px;
    padding: 20px 40px;
    position: relative;
    text-align: center;
  }

  /* com auxílio do chatgpt */
  #main-banner h1::after {
    content: "";
    display: block;
    position: absolute;
    bottom: 28px; /* Ajuste para posicionar a linha abaixo do texto */
    left: 44px;
    width: 100%;
    max-width: 480px;
    height: 3px;
    background-color: #FCBA03;
    opacity: 0;
    transform-origin: left;
    animation: drawLine 1s linear;
  }

  @keyframes drawLine {
  0% {
    transform: scaleX(0);
  }
  50% {
    opacity: 1;
  }
  100% {
    transform: scaleX(1);
    opacity: 0;
  }
}

</style>