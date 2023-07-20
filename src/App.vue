<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />

  <div>

    <input type="text" v-model="search" placeholder="Search">
    <!-- {{ posts }} -->
    <!-- <div v-for="post in  filteredposts " :key="post.id"> -->
    <!-- <div v-for="post in  posts " :key="post.id"> -->
      <table>
        <tr>
          <th>ID</th>
          <th>TITLE</th>
          <th>BODY</th>
        </tr>
        <tr v-for="(post,i) in  filteredposts" :key="post.id"  >
          <div v-if= "i < 50">
          <td>{{ post.id }}</td>
          <td>{{ post.title }}</td>
          <td>{{ post.body }}</td>
        </div>
        </tr>
      </table>
    
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
 
    return {
      search:'',
      posts: [],
    };
  },
  mounted() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then((response) => (this.posts = response.data));
  },
  computed:{
    filteredposts(){
      return this.posts.filter(post=>{ 
        return post.title.match(this.search)})
    }

  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
