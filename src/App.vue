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
import listOfCharacters from "./components/listOfCharacters"


export default {
  name: 'App',
  data(){
    return{

    }
  },
  components: {
  },
  // promises to the api call go here
  mounted(){
    fetch('https://the-one-api.dev/v2/character')
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
