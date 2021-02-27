<template>
  <div id="app">
    <h1 class="title">Lord Of The Rings</h1>
    <div class="main_container">
      <h2>Select a Character:</h2>
      <label for="select_character"></label>
      <select id="character_select" v-model="characterSelected">
        <option disabled value=""> Please Select Somebody</option>
        <!-- <option v-for="(character, index) in characters" 
        :value="character" : key="index">{{character.name}}</option> -->

      </select>
    </div>

    <button class="add_button" v-on:click="addToFavourites">Add Character</button>


  </div>
</template>

<script>
import {eventBus} from './main'
// import listOfCharacters from "./components/listOfCharacters"


export default {
  name: 'App',
  data(){
    return{
      api_key: 'wA9x06TjC7oGabws_5tn',
      url_base: 'https://the-one-api.dev/v2/character',
      query: ''

    }
  },
  components: {
  },
  // promises to the api call go here
  mounted(){
    fetch(`${this.url_base}character?q=${this.query}&APPID=${this.api_key}`)
  .then(res => res.json())
  .then(characters => this.characters = characters)




  eventBus.$on('character-selected', (character) => {
    this.characterSelected = character
})

  },
  methods:{
    
  }

}
</script>

<style>
</style>
