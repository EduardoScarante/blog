<script>
import { RouterLink, RouterView } from 'vue-router'
import '@/assets/main.css'

export default {
  data() {
    return {
      posts: [
        {
          title: 'Primeiro Post',
          content: 'Conteudo do post :)',
          datetime: '15/5/2023'
        },
        {
          title: 'Meu Segundo Post',
          content: 'Conteudo do segundo post :)',
          datetime: '15/5/2023'
        }
        ,
        {
          title: 'Esse é o Terceiro Post',
          content: 'Conteudo do Terceiro post :)',
          datetime: '16/5/2023'
        },
        {
          title: 'Pode ser que essa seja o quarto Post',
          content: 'Conteudo do quarto post :(',
          datetime: '16/5/2023'
        },
        {
          title: 'Esse eu tenho certeza que é o quinto post',
          content: 'Conteudo do quinto post :)',
          datetime: '16/5/2023'
        }
      ]
    }
  },
  methods: {
    addPost(objeto) {
      this.posts.push(objeto)
    }
  }
}

</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home
      </RouterLink>
      <RouterLink to="/create">Novo Post</RouterLink>
    </nav>
  </header>

  <!-- ESCUTA EVENTO E RECEBE OBJETO NA FUNÇÂO ADDPOST -->
  <RouterView :posts="posts" @create-post="addPost" />
</template>

<style>
nav {
  width: 100%;
  text-align: center;
  padding: 10px;
  font-weight: 200;

  box-shadow: 4px 4px 15px lightgray;

}

nav a{
  color: gray;
  text-decoration: none;
  margin: 10px;
}

nav a.router-link-exact-active {
  color: black;
  font-weight: 800;
}


</style>
