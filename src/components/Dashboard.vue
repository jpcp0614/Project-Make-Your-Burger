<template>
  <div id="burger-table">
    <div>
      <div class="" id="burger-table-heading">
        <div class="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Opcionais:</div>
        <div>Ações:</div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
        <div class="order-number">{{ burger.id }}</div>
        <div>{{ burger.name }}</div>
        <div>{{ burger.bread }}</div>
        <div>{{ burger.meat }}</div>
        <div>
          <ul>
            <li v-for="(optional, index) in burger.optionals" :key="index">{{ optional }}</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status">
            <option value="">Status</option>
          </select>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

  const urlBurgers = 'http://localhost:3000/burgers';

  async function getOrders () {

    const req = await fetch(urlBurgers);
    const data = await req.json();

    this.burgers = data;

    console.log(this.burgers);

    // resgatar status
  }

  export default {
    name: 'Dashboard',
    data() {
      return {
        burgers: null,
        burger_id: null,
        status: []
      }
    },
    methods: {
      getOrders,
    },
    mounted() {
      this.getOrders();
    }
  }

</script>

<style scoped>

  #burger-table {
    margin: 0 auto;
    max-width: 1200px;
  }

  #burger-table-heading,
  #burger-table-rows,
  .burger-table-row {
    display: flex;
    flex-wrap: wrap;
  }

  #burger-table-heading {
    border-bottom: 3px solid #333;
    font-weight: bold;
    padding: 12px;
  }

  #burger-table-heading div,
  .burger-table-row div {
    width: 19%;
  }

  .burger-table-row {
    border-bottom: 1px solid #ccc;
    padding: 12px;
    width: 100%;
  }

  #burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 5%;
  }

  select {
    margin-right: 12px;
    padding: 12px 6px;
  }

  .delete-btn {
    background-color: #222;
    border: 2px solid #222;
    color: #FCBA03;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    margin: 0 auto;
    padding: 10px;
    transition: .5s;
  }

  .delete-btn:hover {
    background-color: transparent;
    color: #222;
  }

</style>