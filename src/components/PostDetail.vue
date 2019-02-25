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
  margin-top: 150px;
  margin-bottom: 100px;
  color: white;
  padding: 30px;
  border-radius: 30px;
  background-color: #252525;
  max-width: 600px;
  min-width: 600px;
  height: 750px;
  box-shadow: 1px 1px 20px 6px black;
}

p {
  margin: 10px;
}

img {
  display: block;
  width: 350px;
  height: 450px;
  margin: auto;
  margin-bottom: 50px;
}

</style>
