<script>
import { RouterLink, RouterView } from 'vue-router'
import '@/assets/main.css'
import catLottie1 from "@/assets/lottie/cat1.json"


export default {
  data() {
    return {
      posts: [
        {
          title: 'O gato dorme a maior parte do tempo...',
          content: 'Para quem acha que gatos dormem demais, isso é verdade. Pelo menos ⅔ do dia são muito bem gastos com o sono. Isso significa que em 12 anos, o gato só passa 4 anos acordado.',
          datetime: '15/05/2023 - 09:00'
        },
        {
          title: 'O ronronar do gato faz bem para a saúde!',
          content: 'Ronronar é uma maneira de o felino comunicar algum sentimento. Em alguns casos, ele pode estar sentindo dor, mas, na maioria das vezes, o ronronar demonstra prazer em estar com você. A outra boa notícia é que esse ronronar faz bem para a saúde humana. De acordo com alguns cientistas, vibrações em torno de 18 e 38 Hz, podem auxiliar o organismo na recuperação até de ossos e tecidos.',
          datetime: '16/05/2023 - 09:00'
        }
        ,
        {
          title: 'Gatos são animais muito leais!',
          content: 'Quem pensa que gato é interesseiro não sabe que, na verdade, eles são muito leais aos seus companheiros de casa. Eles gostam de dormir com seus humanos e são companheiros em suas tarefas até na hora que o tutor vai ao banheiro.',
          datetime: '16/5/2023'
        }/*,
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
        },
        {
          title: 'Já esse, podemos concluir sim que é o décimo post',
          content: 'Conteudo do décimo post :)',
          datetime: '19/5/2023'
        } */
      ],
      catLottie1: catLottie1,
    }
  },
  methods: {
    addPost(objeto) {
      this.posts.push(objeto)
    },
    updatePost(updatedPost, id) {

      this.posts[id] = updatedPost
    },
    deletePost(id) {
      this.posts.splice(id, 1);
    },
    redictTo(){
      window.open("https://eduardoscarante.github.io/vuePesonalSite/")
    }
  }
}

</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">
        <span class="material-symbols-outlined">
          home
        </span>
      </RouterLink>
      <RouterLink to="/create">
        <span class="material-symbols-outlined">
          add
        </span>
      </RouterLink>
    </nav>
  </header>

  <!-- ESCUTA EVENTO E RECEBE OBJETO NA FUNÇÂO ADDPOST -->
  <main>
    <RouterView :posts="posts" @create-post="addPost" @edit-post="updatePost" @delete-post="deletePost"/>
  </main>

  <div class="iframe-box">
    <lottie-player class="lottie-player" :src="catLottie1" background="transparent" loop autoplay @click="redictTo"></lottie-player>
  </div>
</template>

<style scoped>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;

  height: 50px;
  width: 100%;

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

.iframe-box {
  position: absolute;
  top: -83px;
  left: 60%;
  width: 250px;
}

@media (max-width: 600px) {

  .iframe-box {
    display: none;
  }
}
</style>
