<template lang="html">
  <div>
    <h2>{{ post.title }}</h2>
    <img :src="post.url" alt="">
    <p>Posted By: {{ post.author }}</p>
    <p>Comments: {{ post.num_comments }}</p>
    <p>Upvotes: {{ post.ups }}</p>
  </div>
</template>

<script>
export default {
  name: "postDetail",
  props: ["post"]
}
</script>

<style lang="css" scoped>

img {
  width: 500px;
  height: 500px;
}

</style>
