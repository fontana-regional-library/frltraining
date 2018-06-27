<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
     <!--  <product v-for="post in posts">
      </product> 
    
          <post 
          audience="kids" 
          content="This is come more content" 
          :id="1234" 
          title="I hope this worked" 
          type="event" showComments="true"/>
             <post 
        audience="teens" 
        title="Hellooooo" 
        content="Another Post" 
        type="post" 
        :id="4567"/>
        -->
<ul>
  <li v-for="post in posts">
    <post :audience="post.audience" :title="post.title" :type="post.type" :content="post.content"></post>
  </li>
  </ul>

  </div>
</template>

<script>
import axios from 'axios';
//var fposts = null;
//        axios.get('http://maconlibraryfriends.org/wp-json/wp/v2/posts')
 //           .then( function(response){
 //            console.log(response.data);
 //               return response;
  //              fposts = response.data;
 //           })
import Vue from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import Product from './components/Product.vue'
import Post from './components/Post.vue'
Vue.component('product', Product)
export default {
  name: 'app',
  components: {
    HelloWorld, Product, Post
  },
  data: () => {
    return {
      posts: [
        {
          audience:'kids',
          title:'Heythere',
          type: 'event',
          content: 'come content',
          example: {
            content: "hello"
          },
        },
        {
          audience:'adults',
          title:'Heythere',
          type: 'event',
          content: 'come content',
        },
        {
          audience:'teens',
          title:'Heythere',
          type: 'event',
          content: 'come content',
        },
      ]
    }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
