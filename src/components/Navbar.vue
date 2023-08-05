<template>
  <nav>
    <router-link to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo-img">
    </router-link>

    <router-link to="/">Home</router-link><span id="span-space"></span>
    <router-link to="/pedidos">Pedidos</router-link>
  </nav>
</template>

<script>
  export default {
    name: 'Navbar',
    props: ['logo', 'alt']
  }
</script>

<style scoped>
  nav {
    align-items: center; /* elementos alinhados no centro, verticalmente */
    background-color: #222;
    border-bottom: 4px solid #111; /* quase preto */
    display: flex; /* manipular os elementos filhos */
    justify-content: flex-end; /* tudo para a direita */
    padding: 15px 50px; /* 15px -> sup e inf, 50px -> dir e esq */
  }

  nav #logo-url {
    margin: auto;
    margin-left: 0; /* joga a logo para a esquerda */
  }

  #logo-img {
    filter: brightness(90%);
    filter: contrast(80%);
    height: 40px;
    width: 40px;
  }

  #span-space {
    border: 1px solid #fff;
    height: 25px;
  }

  nav a {
    color: #FCBA03;
    font-size: 22px;
    margin: 5px 10px 5px 10px;
    text-decoration: none; /* remove o underline */
    text-shadow: black 0.1em 0.1em 0.2em;
    transition: 0.4s;
  }

  nav a:hover {
    color: #fff;
  }
</style>