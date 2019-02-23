<template lang="html">
  <div>
    <p>{{ post.title }}</p>
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

div {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: auto;
  color: white;
  padding: 30px;
  border-radius: 30px;
  background-color: #252525;
  max-width: 450px;
  min-width: 450px;
  height: 750px;
}

img {
  width: 500px;
  height: 500px;
}

</style>
