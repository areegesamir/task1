<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
   
  </div>
</template>

<script>
// import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  axios:({
    method:'post',
    url:'https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js',
    data:{
      title:'article title',
      body:'article body',
      userid:1,
    },

  })
}
</script>



<style scoped>

</style>
