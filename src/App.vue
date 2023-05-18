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
        },
        {
          title: 'Quiça esse é o sexto post',
          content: 'Conteudo do sexto post :)',
          datetime: '18/5/2023'
        },
        {
          title: 'Dúvido muito que esse seja o sétimo post',
          content: 'Conteudo do sétimo post :)',
          datetime: '18/5/2023'
        },
        {
          title: 'Esse não é o oitavo post',
          content: 'Conteudo do oitavo post :)',
          datetime: '18/5/2023'
        },
        {
          title: 'E muito menos esse o nono post',
          content: 'Conteudo do nono post :)',
          datetime: '18/5/2023'
        },
        {
          title: 'Já esse, podemos concluir sim que é o décimo post',
          content: 'Conteudo do décimo post :)',
          datetime: '18/5/2023'
        }
      ]
    }
  },
  methods: {
    addPost(objeto) {
      this.posts.push(objeto)
    },
    updatePost(updatedPost, id) {
      this.posts[id] = updatedPost
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
  <main>
    <RouterView 
    :posts="posts" 
    @create-post="addPost" 
    @edit-post="updatePost"
    />
  </main>
</template>

<style>
nav {
  width: 100%;
  text-align: center;
  padding: 10px 0px;
  font-weight: 200;

  box-shadow: 4px 4px 15px lightgray;

}

nav a {
  color: gray;
  text-decoration: none;
  margin: 10px;
}

nav a.router-link-exact-active {
  color: black;
  font-weight: 800;
}
</style>
