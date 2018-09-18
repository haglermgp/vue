<template>
  <div id="app" >
    <header>{{ title }}</header>
    <form v-on:submit.prevent="addItem" v-on:keypress.enter='addItem'>
      <input
        type="text"
        v-model='input'
        @focus='buttonDisabled = false'
        @blur='buttonDisabled = true'
      >
      <button v-bind:disabled='buttonDisabled' >{{buttonText}}</button>
    </form>
    <ul>
      <li v-for='(dino, index) in dinos' >
        {{ dino.text }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'DINOSAURS',
      input: '',
      buttonText: 'Add Dinosour',
      buttonDisabled: true,
      dinos: [
        { text: 'Terosaurio', quantity: 5 },
        { text: 'Rex', quantity: 4 },
        { text: 'Pet saurio', quantity: 0 },
        { text: 'God zaurio', quantity: 10 }
      ],
    }
  },
  watch: {
    input: function() {
      setTimeout(() => {  
        this.buttonText = this.input !== '' ? 'Add ' + this.input : 'Add Dinosour'
      }, 250)
    }
  },
  methods: {
    addItem() {
      if (this.input !== '') {
        this.dinos.push( { text: this.input, quantity: 0 } )
      };
      this.input = ''
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
  }

  ul {
    list-style-type: none;
  }

  li {
    width: 300px;
    border: 2px solid grey;
    border-radius: 8px;
    margin: 8px;
    margin: 8px auto;
    padding: 8px;
  }

  a {
    color: blue;
    text-decoration: none;
  }
</style>
