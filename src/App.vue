<template lang="html">
  <div>
    <h1><img src="https://vignette.wikia.nocookie.net/beastsaga/images/1/10/Reddit.png/revision/latest?cb=20170808093108" alt=""> Meme ReVue <img src="https://png2.kisspng.com/sh/c20ef0795fa10628cd73a5b8b70d8141/L0KzQYm3V8E1N5ZvfZH0aYP2gLBuTgZ2bV5vi59zYYbkg7T5igB1NZ1ueuRqcomwd7r7iQVjNZd3fddFaX7qPcH2if51NWZnTKsDY0e2R4e4UBQ4NmUASqMBMkG8QYa6UcU1Pmg4UaYDM0exgLBu/kisspng-vue-js-javascript-library-github-freezing-point-5b498c737613d7.4921621915315467394837.png" alt=""></h1>

    <button v-if="selectedPost" v-on:click="showAll">Show all</button>
    <button v-if="!selectedPost" v-on:click="clearNew">Top Memes</button>
    <new-posts v-if="!selectedPost"/>

    <post-search v-if="!selectedPost && !newPosts" :posts="posts"/>

    <post-list v-if="!selectedPost && !foundPosts && !newPosts" :posts="posts"/>
    <post-list v-if="foundPosts && !selectedPost && !newPosts" :posts="foundPosts"></post-list>
    <post-list v-if="!selectedPost && newPosts" :posts="newPosts"></post-list>


    <post-detail v-if="selectedPost" :post="selectedPost"/>
  </div>
</template>

<script>
import { eventBus } from "./main.js"
import PostList from "./components/PostList.vue"
import PostSearch from "./components/PostSearch.vue"
import PostDetail from "./components/PostDetail.vue"
import NewPosts from "./components/NewPosts.vue"
export default {
  name: "app",
  data(){
    return {
      posts: [],
      selectedPost: null,
      foundPosts: null,
      newPosts: null
    }
  },
  methods: {
    showAll(){
      this.selectedPost = null;
    },
    clearNew(){
      this.newPosts = null
      window.scrollTo(0,0)
    },
    resetFound(){
      this.foundPosts = null;
    }
  },
  components: {
    "post-list": PostList,
    "post-detail": PostDetail,
    "post-search": PostSearch,
    "new-posts": NewPosts,
  },
  mounted(){
    fetch("https://www.reddit.com/r/memes/.json?limit=50")
      .then(result => result.json())
      .then(result => result.data.children)
      .then(posts => {
        this.posts = posts.filter((post) => {
          return post.data.url.includes(".jpg")
        })})


      eventBus.$on("selected-post", (post) => {
        this.selectedPost = post
      })

      eventBus.$on("found-posts", (posts) => {
        this.foundPosts = posts
      })

      eventBus.$on("new-posts", (posts) => {
        this.newPosts = posts
      })
  }
}
</script>

<style lang="css" scoped>

h1 {
  text-align: center;
  padding: 10px;
  background-color: #252525;
  color: white;
  font-size: 70px;
  margin-top: 0;
  border-radius: 0 0 40px 40px;
  text-shadow: 3px 4px 20px black;
  width: -webkit-fill-available;
  position: fixed;
  top: 0;
}

input {
  position: fixed;
  top: 200px;
}

button {
  position: fixed;
  top: 130px;
  left: 40px;
  background: #333;
  color: white;
}

h1 img {
  width:50px;
  height: 50px;
}

html {
  margin-top: 0;
}

</style>
