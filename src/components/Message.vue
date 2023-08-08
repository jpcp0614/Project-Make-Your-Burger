<template>
  <div class="message-container">
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  name: 'Message',
  props: {
    msg: String,
  }
}
</script>

<style scoped>
  .message-container {
    background-color: #CCE5FF;
    border: 2px solid #B8DAFF;
    border-radius: 5px;
    color: #004085;
    margin: 30px auto;
    max-width: 400px;
    padding: 10px;
  }

</style>