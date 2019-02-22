<template lang="html">
  <div>
    <h1>Memes</h1>

    <button v-if="selectedPost" v-on:click="showAll">Show all</button>

    <post-search :posts="posts"/>

    <post-list v-if="!selectedPost && !foundPosts" :posts="posts"/>
    <post-list v-if="foundPosts && !selectedPost" :posts="foundPosts"></post-list>


    <post-detail v-if="selectedPost" :post="selectedPost"/>
  </div>
</template>

<script>
import { eventBus } from "./main.js"
import PostList from "./components/PostList.vue"
import PostSearch from "./components/PostSearch.vue"
import PostDetail from "./components/PostDetail.vue"
export default {
  name: "app",
  data(){
    return {
      posts: [],
      selectedPost: null,
      foundPosts: null
    }
  },
  methods: {
    showAll(){
      this.selectedPost = null;
    }
  },
  components: {
    "post-list": PostList,
    "post-detail": PostDetail,
    "post-search": PostSearch
  },
  mounted(){
    fetch("https://www.reddit.com/r/memes/.json?limit=100")
      .then(result => result.json())
      .then(result => result.data.children)
      .then(posts => this.posts = posts)


      eventBus.$on("selected-post", (post) => {
        this.selectedPost = post
      })

      eventBus.$on("found-posts", (posts) => {
        this.foundPosts = posts
      })



  }
}
</script>

<style lang="css" scoped>


</style>
