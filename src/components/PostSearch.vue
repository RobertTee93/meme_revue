<template lang="html">
  <div>
    <label>Search posts</label>
      <input v-on:keyup="handleSearch" v-on:keyup.return="showPosts" type="text" v-model="input">
  </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
  name: "postSearch",
  props: ["posts"],
  data(){
    return {
      input: "",
      foundPosts: []
    }
  },
  methods: {
    handleSearch(){
      this.foundPosts = this.posts
      .filter((post) => post.data.title.toLowerCase()
      .includes(this.input.toLowerCase()))

      eventBus.$emit("found-posts", this.foundPosts)


    }
  }
}
</script>

<style lang="css" scoped>
</style>
