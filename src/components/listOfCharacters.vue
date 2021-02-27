<template>
<div v-if="characters">
    <ul>
        <list-item v-for="(character, index) in characters" :character="character" :key="index"></list-item>
    </ul>
</div>
  
</template>

<script>
// import listItem from './listItem'

export default {
    name: "listOfCharacters",
    props: ["characters"],
    components: {
        // "list-item":listItem
    }

}
</script>

<style>

</style>