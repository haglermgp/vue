<template>
  <div id="app" >
    <header>{{ title }}</header>
    <div class="canvas-button" >
      <button
        v-bind:class="[sizeToggle ? 'large' : '', { 'rounded': isRounded }]"
        v-bind:disabled="disabled"
        v-bind:style="styles"
      >
        Start Tour
      </button>
    </div>
    <hr>
    <h4>Options</h4>

    <ul>
      <li>
        <input type="checkbox" v-model='sizeToggle' >
        <label>Large</label>
      </li>
      <li>
        <input type="checkbox" id='round' v-model='isRounded' >
        <label for='round' >Rounded</label>
      </li>
      <li>
        <input type="checkbox" v-model='disabled' >
        <label>Disabled</label>
      </li>
      <li>
        <input type="text" v-model='backgroundColor' >
        <label>Background Color</label>
      </li>
      <li>
        <input type="text" v-model='fontColor' >
        <label>Font Color</label>        
      </li>
      <li>
        <input type="range" min='15' max='85' v-model='range' >
        <label>Position</label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'Style Bindings',
      isRounded: false,
      sizeToggle: false,
      disabled: false,
      backgroundColor: '#ccc',
      fontColor: '#000',
      range: 50,  
    }
  },
  computed: {
    styles: function() {
      return {
        color: this.fontColor,
        background: this.backgroundColor,
        'margin-left': this.range + "%"
      }
    }
  }
}

</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
  }

  header {
    text-align: center;
  }

  ul {
    list-style-type: none;
  }

  #app {
    width: 400px;
    border: 2px solid grey;
    border-radius: 8px;
    margin: 8px;
    margin: 8px auto;
    padding: 8px;
  }

  li {
    height: 40px;
    text-align: left;
  }

  ul label {
    margin-left: 10px;
    font-weight: bold;
    font-size: 13px;
    color: grey;
  }

  .large {
    width: 120px;
    height: 50px;
  }

  .canvas-button {
    height: 60px;
  }

  .canvas-button button {
    margin-top: 10px;
  }

  .rounded {
    border-radius: 12px;
  }

</style>
