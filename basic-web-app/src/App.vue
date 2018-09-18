<template>
  <div id="app" >
    <header>{{ title }}</header>
    <form v-on:submit.prevent="addItem">
      <input type="text" name='dino' >
      <button >Add Dinosaur</button>
    </form>
    <ul>
      <li v-for='(dino, index) in dinos' >
        <button v-on:click='addDino(index)'>+</button>
        {{ dino.quantity }}
        <button v-on:click='decreaseDino(dino.quantity, index)'>-</button>
        {{ dino.text }}
        <button >make extinct</button>
      </li>
    </ul>
    <div>
      <ul>
        <li>Total Dinosaurs: {{ totalDinos }} <b> Dinos Updated {{dinosUpdated}}</b></li>
        <li>Total Species: {{ totalSpecies }} <b> Species Updated {{speciesUpdated}}</b></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'DINOSAURS',
      dinosUpdated: 0,
      speciesUpdated: 0,
      dinos: [
        { text: 'Terosaurio', quantity: 5 },
        { text: 'Rex', quantity: 4 },
        { text: 'Pet saurio', quantity: 0 },
        { text: 'God zaurio', quantity: 10 }
      ],
    }
  },
  methods: {
    addItem(value) {
      let newDino = value.target[0]
      if (newDino.value !== '') {
        this.dinos.push({
          text: newDino.value,
          quantity: 0
        })
        newDino.value = ''
      };
    },
    addDino(index) {
      this.dinos[index].quantity += 1
    },
    decreaseDino(value, index) {
      if (value > 0) {
        this.dinos[index].quantity -= 1        
      };
    }
  },
  computed: {
    totalDinos() {
      this.dinosUpdated += 1;
      var sum = 0;
      var dinos = this.dinos;

      dinos.forEach((element) => {
        sum += element.quantity;
      })

      return sum
    },
    totalSpecies() {
      this.speciesUpdated += 1;
      var sum = 0;
      var dinos = this.dinos;
      return sum = dinos.length
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
