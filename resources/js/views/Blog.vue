<template>
    <div>
        <spin v-if="loading"></spin>
        <div v-else style="display: flex; flex-wrap: wrap;">
            <post
                v-for="post in posts"
                v-bind:key="post.id"
                :title="post.title"
                :body="post.body"
                :date="post.date"
                :image="post.image"
                :id="post.id"
            />
        </div>
    </div>
</template>


<script>

    import Spin from "../components/Spin";
    import axios from 'axios';
    import Post from "../components/Blog/Post";

    export default {
        components: {
            Spin,
            Post
        },
        data: () => ({
            loading: true,
            posts: []
        }),
        mounted() {
            this.loadPosts();
        },
        methods: {
            loadPosts() {
                axios.get('/api/posts')
                .then(res => {
                    this.posts = res.data;
                    this.loading = false;
                })
            }
        }
    }
</script>

<style scoped>
    /*.uk-card {*/
    /*    width: 40%;*/
    /*    margin-right: 20px;*/
    /*    margin-bottom: 20px;*/
    /*}*/
    /*.uk-card:last-child {*/
    /*    margin-right: 0;*/
    /*}*/
</style>
