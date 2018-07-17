<template>
    <article :id="id">
        <h2>{{ title }}</h2>

        <p v-if="isYoungAdultEvent">
            Show this only if it is a teen's event!
        </p>

        {{ content }}


        <h3>Comments</h3>
        <button v-if="!showComments"
                v-on:click="toggleCommentSection">Show Comments</button>
        <section class="comments" v-if="showComments === true">
            {{ comments }}
        </section>
    </article>
</template>

<script>
export default {
  name: 'post',

  computed: {
    isYoungAdultEvent() {
      if (this.audience === 'teens' && this.type === 'blog') {
        return true;
      } else {
        return false;
      }
    }
  },

  data: () => {
    return {
      heading: 'Hi',
      showComments: false,
      comments: [],
    };
  },

  methods: {
    getCommentFromWordPress() {
      // 1. Reaching out to an api
      // 2. Getting the post from that call
      const commentFromAPI = {
        id: 3,
        comment: 'balh blah lah',
      };

      // 3. Inserting the post into data ^.

      this.comments.push(commentFromAPI);
    },
    nameOfMethod: function() {},

    toggleCommentSection() {
      this.showComments = true;
    },
  },

  props: {
    audience: String,
    content: {
      default: 'some contnet here',
      type: String,
    },
    title: String,
    type: String,
    id: {
      default: 0,
      type: Number,
    },
  },
};
</script>

<style>
 h2 {
     color: red;
 }
</style>
