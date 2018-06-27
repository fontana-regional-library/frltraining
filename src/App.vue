<template>

  <div id="app">

    <img src="./assets/logo.png">

    <ul>
      <li v-bind:key="post.title" v-for="post in posts">
        <post :audience="post.audience"
              :content="post.content"
              :title="post.title"
              :type="post.type"></post>
      </li>
    </ul>

  </div>

</template>

<script>
import Post from './components/Post';

export default {
  name: 'app',
  components: {
    Post,
  },

  data: () => {
    return {
      posts: [
        {
          audience: 'dogs',
          title: 'I am for dogs',
          type: 'blog',
          content: 'Dogs are sweet',
        },
        {
          audience: 'kids',
          title: 'Hey there',
          type: 'event',
          content: 'some content',
        },
        {
          audience: 'teens',
          title: 'Hey there 2',
          type: 'blog',
          content: 'some content',
        },
        {
          audience: 'kids',
          title: 'Hey there 3',
          type: 'event',
          content: 'some content',
        },
        {
          audience: 'adult',
          title: 'Hey there 4',
          type: 'blog',
          content: 'some content',
        }
      ]
    };
  }
};
</script>

<style>

</style>
