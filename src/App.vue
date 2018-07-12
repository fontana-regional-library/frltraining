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
<ul class="posts">
  <li v-for="post in posts" :key="post.id">
    <post :audience="post.type" :title="post.title.rendered" :type="post.slug" :content="post.content.rendered"></post>
  </li>
  </ul>
<!-- <button v-on:click="getPagesFromWordPress">Click me</button> -->
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
//AJAX 


Vue.component('product', Product)
export default {
  name: 'app',
  components: {
    HelloWorld, Product, Post
  },
  data: () => {
    return {
      posts: []
    };
  },
  methods:{
    getPagesFromWordPress() {
      axios.get('https://fontana.librarians.design/wp-json/wp/v2/pages')
      // HTTP Status Codes
      // 404 = not found
      // 200 = Success!
        .then( ( {data: pages, status} ) => {
/*        console.log(data.data); 
          const pages = data.data;
          console.log(pages); */
          console.log(pages);
          console.log(status);
          //this.posts = pages;
          this.$set(this, 'posts', pages);
        }) //if Successful, DO THIS
        .catch(error=> {
          console.log(error);
        }); //if not, DO THIS
    },
    sanitizeContent() {
      //
    }
  },
  mounted() {
    this.getPagesFromWordPress();
  },
   /*  return {
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
    } */
};
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
.posts {
  text-align:left;
}
</style>
