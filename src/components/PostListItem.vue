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
}

img {
  width: 350px;
  height: 450px;
  margin-bottom: 50px;
}

h2 {
  text-align: center;
  margin-bottom: 30px;
}

</style>
