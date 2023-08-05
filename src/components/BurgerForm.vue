<template>
  <div>
    <p>Componente de mensagem</p>
    <div>
      <form id="burger-form" @submit="createBurger">

        <div class="input-container">
          <label for="name-id">Nome do cliente:</label>
          <input type="text" id="name-id" name="name" v-model="name_client" placeholder="Digite seu nome aqui">
        </div>
  
        <div class="input-container">
          <label for="bread-id">Escolha o pão:</label>
          <select name="bread-name" id="bread-id" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option v-for="bread in breads" :key="bread.id" :value="bread.type">{{ bread.type }}</option>
          </select>
        </div>

        <div class="input-container">
          <label for="meat-id">Escolha a carne:</label>
          <select name="meat-name" id="meat-id" v-model="meat">
            <option value="">Selecione o tipo de carne</option>
            <option v-for="meat in meats" :key="meat.id" :value="meat.type">{{ meat.type }}</option>
          </select>
        </div>

        <div id="opcionais-container" class="input-container">
          <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
          <div class="checkbox-container" v-for="optional in optional_data" :key="optional.id">
            <input type="checkbox" name="optionals-name" v-model="optionals" :value="optional.type">
            <span>{{ optional.type }}</span>
          </div>
        </div>

        <div class="input-container">
          <input type="submit" class="submit-btn" value="Criar meu Burger">
        </div>

      </form>
    </div>
  </div>
</template>

<script>

const url = 'http://localhost:3000/ingredients';

export default {
  name: "BurgerForm",
  data() {
    return {
      //* json data
      breads: null, 
      meats: null,
      optional_data: null,
      //* ----------------

      //* enviar para o backend
      name_client: null,
      bread: null,
      meat: null,
      optionals: [],
      msg: null,
      //* ----------------
    }
  },
  methods: {
    async getIngredients() {
      const req = await fetch(url);
      const data = await req.json();

      this.breads = data.breads;
      this.meats = data.meats;
      this.optional_data = data.optionals;
    },
    async createBurger(e) {
      e.preventDefault();

      const data = {
        name: this.name_client,
        bread: this.bread,
        meat: this.meat,
        optionals: Array.from(this.optionals),
        status: "Solicitado",
      }
      console.log(data);
    }
  },
  mounted() {
    this.getIngredients();
  }
}
</script>

<style scoped>

  #burger-form {
    align-items: center;
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    max-width: 400px;
  }

  .input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
  }

  label {
    border-left: 4px solid #FCBA03;
    color: #222;
    font-weight: bold;
    margin-bottom: 15px;
    padding: 5px 10px;
  }

  input, select {
    padding: 5px 10px;
    width: 300px;
  }

  #opcionais-container {
    flex-direction: row;
    flex-wrap: wrap;
  }

  #opcionais-title {
    margin: 0 0 20px 50px;
    width: 100%;
  }

  .checkbox-container {
    align-items: flex-start;
    display: flex;
    margin-bottom: 20px;
    margin-left: 50px;
    width: 100%;
  }

  .checkbox-container span,
  .checkbox-container input {
    width: auto;
  }

  .checkbox-container span {
    font-weight: bold;
    margin-left: 6px;
  }

  .submit-btn {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 3px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }

  .submit-btn:hover {
    background-color: transparent;
    color: #222;
  }

</style>