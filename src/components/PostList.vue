<template lang="html">
    <div id="post-container">
      <post-list-item v-for="(post, index) in posts" :key="index" :post="post"></post-list-item>
    </div>
</template>

<script>
import PostListItem from "./PostListItem.vue"

export default {
  name: "postList",
  props: ["posts"],
  components: {
    "post-list-item": PostListItem
  }
}
</script>

<style lang="css" scoped>

#post-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 0 100px;
}

</style>
