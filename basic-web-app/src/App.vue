<template>
  <div id="app" >
    <input type="checkbox" id='checkbox' v-model="checked" />
    <label for="checkbox">
      This box is <b> {{ checked ? 'checked' : 'uncheked'}} </b>
    </label>
    <hr>
    <template v-for='dino in dinos' >
      <label>
        <input type="radio" v-bind:value="dino" v-model="chosenDino" >
        {{ dino }}
      </label>
    </template>
    <br>
    <span>Favorite: {{ chosenDino }}</span>
    <hr>

    <select v-model="selectedPeriods" multiple>
      <option v-for="period in periods" v-bind:value="period.value">
        {{ period.name }} - {{ period.value }}
      </option>
    </select>
    <br>
    <span>Selected Period Value: {{ selectedPeriods }}</span>

    <hr>
    <input type="text" v-model="single" />
    <p style="white-space: pre;">{{ single }}</p>
    <hr>
    <textarea v-model="message" placeholder="add multiple lines" ></textarea>
    <p style="white-space: pre;" >{{ message }}</p>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      checked: false,
      chosenDino: '',
      selectedPeriods: [],
      single: '',
      message: '',
      dinos: [
        "Triceratops", "Velociraptor", "Tyrannosaurus"
      ],
      periods: [
        { name: 'Triassic', value: 1 },
        { name: 'Jurasic', value: 2 },
        { name: 'Cuaternary', value: 3 },
      ]
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
