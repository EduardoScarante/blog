<script>


export default {
    props: {
        posts: Array
    },
    data() {
        const id = this.$route.params.id

        return {
            id: id,
            post: this.posts[id],
        }
    },
    methods: {
        detalhes(id) {
            console.log(id);
            this.$router.push(`/edit/${id}`)
        },
        deletePost(id) {

            if (confirm("Deletar?")) 
            {
                this.$emit("delete-post", id)
                this.$router.push(`/`)
            }
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="content">
            <h3>{{ post.title }}</h3>

            <textarea :value="post.content" readonly></textarea>
            <h4>{{ post.datetime }}</h4>
        </div>


        <hr>
        <div class="btns">

            <span class="material-symbols-outlined" @click="deletePost(id)">
                delete
            </span>

            <span class="material-symbols-outlined" @click="detalhes(id)">
                edit_note
            </span>
        </div>

    </div>
</template>

<style scoped>
textarea {
    resize: none;
    outline: none;
    border: none;
    width: 100%;
    height: 300px;

    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    font-size: 16px;
}

.container {
    margin: auto;
    margin-top: 15px;

    background-color: white;
    box-shadow: 3px 3px 15px lightgray;
    border: none;

    width: 450px;
    padding: 20px;

    border: 3px;
}

.content h3{
    max-height: 100px;
    overflow: auto;
}

.content h4 {
    font-weight: 100;
    color: #535353;

    text-align: end;

    font-style: italic;
}

.btns {
    display: flex;
    justify-content: space-evenly;
}

@media (max-width: 600px) {
    .container {
        width: 85vw;
    }
}
</style>