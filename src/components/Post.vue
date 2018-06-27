<template>
<div :id="id">
    <h1> {{title}} </h1>
    <p v-if="isKidsEvent">Show this only if it's a kids event</p>
    {{heading}}

    {{isKidsEvent}}
    <p>{{content}}</p>
    <h3>Comments</h3>
    
        <button v-if="!showComments"
                v-on:click="toggleCommentSection">Show Comments</button>
        <section class="comments" v-if="showComments === true">
        {{comments}}
    </section>
    </div>
</template>
<script>
export default {
    data: () => {
        return {
            heading: 'HEEEEELPP',
            comments:[
                {
                    id:1,
                    comment: 'Hello this is wrong',
                }
            ],
            showComments: false
        }
    },
    name: 'post',
    props: {
        title: String,
        type: String,
        audience: String,
        content: {
            default: 'Some content here',
            type: String
        },
        id: {
            default:0,
            type: Number
        }
    },
    computed: {
        isKidsEvent () {
            if(this.audience === 'kids' && this.type === 'event') {
                return true;
            } else {
                return false;
            }
        }
    },
    methods: {
        nameOfMethod: function() {},
        otherMethod () {},
        toggleCommentSection () {
            this.showComments = true;
        },
        getCommentFromWordPress() {
//1. Reaching out to api
//2. Getting post from that call
const commentFromAPI = {
    id:3,
    comment: 'Blah,blah,blah',
};
this.comments.push(commentFromAPI);
//3.Inserting pst
        }
        //getting existing data from an external source- use method
    },
    mounted() {
        // this.toggleCommentSection();
        this.getCommentFromWordPress();
    },
    created() {},
    destroyed() {},
}
</script>
<style></style>