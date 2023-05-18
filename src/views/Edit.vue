<script>

import PostForm from '../components/PostForm.vue';

export default {
    props: {
        posts: Array
    },
    components: {
        PostForm
    },
    data() {
        return {
            post: this.posts[this.$route.params.id],
        }
    },
}
</script>

<template>
    <PostForm :post="post" />

    {{ post }}
</template>

<style></style>