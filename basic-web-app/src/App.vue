<template>
  <div id="app" >
    <header>{{ title }}</header>
    <hr>
    <form v-on:submit.prevent="addDinos">
      <button >Add Dinosaur</button>
      <input type="number" v-model='amount'>
    </form>
    <p>
      You have {{ total }} Dinosours!
    </p>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'Dinosours',
      total: 0,
      amount: null
    }
  },
  methods: {
    addDinos: function() {
      this.total += Number(this.amount);
    }
  }
}

</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    border: 2px solid grey;
    border-radius: 12px;
  }

  a {
    color: blue;
    text-decoration: none;
  }
</style>
