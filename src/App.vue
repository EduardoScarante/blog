<script>
import { RouterLink, RouterView } from 'vue-router'

export default {
  data() {
    return {
      formData: {},
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
      ],
      titleSearch: ''
    }
  },
  methods: {
    submitForm(event) {
      event.preventDefault()

      let now = new Date()
      let dataDaPostagem = `${now.getDate()}/${now.getMonth() + 1}/${now.getFullYear()}`

      this.posts.push({
        title: this.formData.title,
        content: this.formData.content,
        datetime: dataDaPostagem
      })

      this.formData = {}
    },
  },
  computed: {
    filteredPost() {
      /*       
        const listaFinal = []
        for (const post of this.posts) {
          if (post.title.includes(this.titleSearch)) {
            listaFinal.push(post)
          }
        } 
      */

      /* Forma mais reduzida
      return this.posts.filter((item) => item.title.includes(this.titleSearch))
      */

      //Se caso o search estiver vazio, haverá retorno de todos os posts
      // GUARD -> impede que o código seja executado sem que exista real necessidade
      if (!this.titleSearch) return this.posts

      return this.posts.filter((item) => {
        return item.title.includes(this.titleSearch)
      })

    }
  }
}

</script>

<template>
  <form id="form" action="">
    <input v-model="formData.title" placeholder="Título">
    <textarea v-model="formData.content" placeholder="Message"></textarea>

    <button type="submit" @click="submitForm">Criar</button>
  </form>


  <div id="searchBox">
    <input id="searchInput" type="text" v-model="titleSearch" placeholder="Procure pelo título do Post...">
  </div>

  <div id="lista-posts">
    <div class="post center" v-for="x in filteredPost" :key="x.title">
      <h3>{{ x.title }}</h3>
      <h4>{{ x.datetime }}</h4>
      <p>{{ x.content }}</p>
    </div>
  </div>

  <!--   <RouterView /> -->
</template>

<style>
form {
  display: flex;
  flex-direction: column;
  align-items: center;

  margin-bottom: 10px;
}

#searchBox{
  text-align: center;

  border-top: 1px solid #cacaca;

  padding-top: 10px;
}

form>*,
#searchInput {
  background-color: white;
  box-shadow: 3px 3px 15px lightgray;
  border: none;

  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;

  width: 500px;
  padding: 10px;
  margin-top: 5px;

  border: 3px;
}

form button {
  background-color: rgb(53, 53, 53);
  color: whitesmoke;
  font-weight: 800;
  width: 100px;
  border-radius: 10px;

  transition: 0.5s;
}

form button:hover {
  background-color: #2b1a1a;
  box-shadow: 3px 3px 1px lightcoral;
}


#lista-posts {
  width: 100%;
  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  justify-content: center;
}

.post {
  background-color: white;
  height: 200px;
  width: 270px;

  box-shadow: 4px 4px 15px lightgray;

  border-radius: 10px;
  padding: 10px;

  margin: 10px;
}

@media (max-width: 600px) {
  form>*,
  #searchInput {
    width: 87vw;
  }

  .post{
    width: 100vw;
  }
}
</style>
