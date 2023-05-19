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
        const id = this.$route.params.id
        
        return {
            id: id,
            post: this.posts[id],
        }
    },
}
</script>

<template>
    <PostForm :post="post" :id="id"/>
</template>

<style></style>