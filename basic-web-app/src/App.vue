<template>
  <div id="app" >
    <header>{{ title | capitalize }}</header>
    <ul>
      <li v-for='(dino, index) in dinos' class="boxDinos" >
        <h4>{{ dino.text | capitalize }}</h4>
        <span>The <i>{{ dino.text | undercase }}</i> weight {{ dino.weight }}. </span>
        <br>
        <a href="">{{ dino.text | undercase | url }}</a>
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
      title: 'JURASIC PARK',
      dinos: [
        { text: 'Terosaurio', weight: '200 kg' },
        { text: 'Rex', weight: '190 kg' },
        { text: 'Pet saurio', weight: '20 kg' },
        { text: 'God zaurio', weight: '10 kg' }
      ],
    }
  },
  filters: {
    capitalize: (value) => {

      if (!value) return '';
      value = value.toString();

      return value.charAt(0).toUpperCase() + value.slice(1)
    },
    undercase: (value) => {
      if(!value) return '';
        value = value.toString();

        return value.toLowerCase();
    },
    url: (value) => {
      if(!value) return '';
        value = value.toString();

        return 'https://wikipedia.org/wiki/' + value
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

  .boxDinos {
    width: 300px;
    border: 2px solid black;
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
