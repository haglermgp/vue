<template>
  <div id="app" >
    <header>{{ title }}</header>
    <div v-html='description'/>
    <div>
      <input type="text" id='itemForm' v-on:keypress.enter='addItem' />
      <button v-on:click='addItem' >Add Disonaur</button>
    </div>
    <ul>
      <li v-for='(item, index) in items' >
        <button v-on:click='deleteItem(item.text, index)' >X</button>
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  data () {
    return {  
      title: 'VUE COMPONENTS',
      description: 'The dinosaurius <b>World</b> <i>Jurasic</i> Park',
      items: [
        { text: 'Terosaurio' },
        { text: 'Rex' },
        { text: 'Pet saurio' },
        { text: 'God zaurio' }
      ],
    }
  },
  methods: {
    addItem() {
      let input = document.getElementById('itemForm');
      if (input.value !== '') {
        this.items.push({
          text: input.value
        })
        input.value = '';
      };
    },      
    deleteItem(props, index) {
      this.items.splice(index,1)
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
</style>
