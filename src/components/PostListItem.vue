<template lang="html">
  <div class="post" v-on:click="clickHandler">
    <h2>{{ post.data.title }}</h2>
    <img :src="post.data.url" alt="">
  </div>

</template>

<script>
import { eventBus } from "../main.js"

export default {
  name: "postListItem",
  props: ["post"],
  methods: {
    clickHandler(){
      eventBus.$emit("selected-post", this.post.data)
    }
  }
}
</script>

<style lang="css" scoped>

div {
  padding: 30px;
  margin: 30px;
  border-radius: 30px;
  background-color: #252525;
  max-width: 600px;
  min-width: 600px;
  box-shadow: 1px 1px 20px 6px black;
}

img {
  display: block;
  width: 350px;
  height: 450px;
  margin: auto;
  margin-bottom: 50px;
}

h2 {
  text-align: center;
  margin-bottom: 30px;
  margin-top: 0;
}

</style>
