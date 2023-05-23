<script>
import { RouterLink } from 'vue-router'
import catLottie from "@/assets/lottie/cat.json"

export default {
  data() {
    return {
      titleSearch: '',
      showModal: false,
      selectedPost: null,
      selectedId: null,
      catLottie: catLottie,
    }
  },
  props: {
    posts: Array
  },
  computed: {
    filteredPost() {
      // GUARD -> impede que o código seja executado sem que exista real necessidade
      if (!this.titleSearch) return this.posts

      return this.posts.filter((item) => {
        return item.title.includes(this.titleSearch)

        /* Forma mais reduzida
        return this.posts.filter((item) => item.title.includes(this.titleSearch))
        */
      })
    }
  },
  methods: {
    getPostId(title) {
      for (const index in this.posts) {
        const post = this.posts[index]
        if (post.title === title) return index;
      }
    },
    setupModal(id) {
      /* Mostra o Modal */
      this.showModal = !this.showModal

      /* Seta variável conforme parametro da função */
      id ? this.selectedPost = this.posts[id] : this.selectedPost = null
    },
    deletePost() {
      const idToDelete = this.getPostId(this.selectedPost.title)
      this.$emit("delete-post", idToDelete)
      this.showModal = !this.showModal
    },
    detalhes(id) {
      this.$router.push(`/detail/${id}`)
    },
    redictTo(){
      window.open("https://eduardoscarante.github.io/vuePesonalSite/")
    }
  }
}

</script>

<template>
  <div class="container">


    <div class="iframe-box">
      <!-- <iframe src="https://embed.lottiefiles.com/animation/86330"></iframe> -->
      <lottie-player class="lottie-player" :src="catLottie" background="transparent" loop autoplay @click="redictTo"></lottie-player>
    </div>


    <div id="searchBox">
      <input type="text" v-model="titleSearch" placeholder="  Procure pelo título do Post...">
    </div>

    <div id="lista-posts">
      <div class="post center" v-for="x in filteredPost" :key="x.title">
        <div>
          <h3>{{ x.title }}</h3>
          <p>{{ x.content }}</p>
          <h4><i>{{ x.datetime }}</i></h4>
        </div>

        <hr>

        <div class="icons">
          <span class="material-symbols-outlined">
            <RouterLink :to="`/edit/${getPostId(x.title)}`"> edit_note </RouterLink>
          </span>

          <!-- :id="getPostId(x.title)"  -->
          <!-- Setup Modal atribui variável para mostrar dentro do corpo do modal o título do post -->
          <!-- GetPostId retorna a posição da array -->
          <span @click="setupModal(getPostId(x.title))" class="material-symbols-outlined">
            delete
          </span>

          <span class="material-symbols-outlined" @click="detalhes(getPostId(x.title))">
            info
          </span>
        </div>

      </div>
    </div>

    <div class="modal center-modal" v-show="showModal">
      <div class="modal-content center-modal">
        <h3>Deletar Post</h3>
        <hr>
        <p>Tem certeza que deseja deletar o post '{{ selectedPost?.title }}' ?</p>
        <div class="modal-actions center-modal">
          <button class="bg-error" @click="setupModal"> Cancelar </button>
          <button class="bg-sucess" @click="deletePost"> Confirmar </button>
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped>
.container {
  width: 100%;
  max-width: 1280px;

  margin: auto;
}

#searchBox {
  width: 100%;
  text-align: center;

  margin-top: 10px;

}

#searchBox>* {
  /* background-color: white; */
  background-color: white;

  box-shadow: 3px 3px 15px lightgray;
  border: none;

  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;

  width: 520px;
  padding-top: 10px;
  padding-bottom: 10px;

  border: 3px;

}


#lista-posts {
  width: 100%;
  display: flex;
  align-items: center;

  /* flex-wrap: wrap; */

  flex-direction: column;

  justify-content: center;

}

.post {
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  background-color: white;

  width: 500px;

  box-shadow: 4px 4px 15px lightgray;

  margin-top: 10px;
  margin-bottom: 10px;

  padding: 10px;
  padding: 10px;
}

.post h4 {
  font-weight: 100;
  color: #535353;

  text-align: end;
}

.post p,
.post h3 {
  overflow-x: hidden;
  max-height: 200px;
}

.post h3 {
  max-height: 100px;
}

.icons {
  display: flex;
  justify-content: space-around;
}

.icons span:hover {
  cursor: pointer;
}

.icons span a {
  color: black;
  text-decoration: none;
}

.iframe-box {
  width: 250px;
  height: 155px;
  z-index: 1;

  margin: auto;

  display: flex;
  justify-content: center;
  align-items: center;

  position: absolute;
  top: -10px;
  left: 50%;

  overflow: hidden;
}

.lottie-player {
  border: none;
  height: 500px;
  width: 100%;
}

@media (max-width: 600px) {

  #searchBox>* {
    width: 95%;
    border-radius: 5px;
  }

  .post {
    width: 90vw;

    padding: 10px;
  }

  .lottie-player , .iframe-box{
    display: none;
  }
}
</style>
