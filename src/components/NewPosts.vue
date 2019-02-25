<template lang="html">
  <button v-on:click="getNewPosts">New Memes</button>
</template>

<script>
import { eventBus } from "../main.js"
export default {
  name: "newPosts",
  methods: {
    getNewPosts(){
      fetch("https://www.reddit.com/r/memes/new/.json")
      .then(result => result.json())
      .then(posts => posts.data.children)
      .then(posts => {
        eventBus.$emit("new-posts", posts)
        window.scrollTo(0,0)
      })

      }
    }
  }
</script>

<style lang="css" scoped>
button {
  position: fixed;
  top: 130px;
  left: 120px;
  background: #333;
  color: white;
}

</style>
