<script>
import { RouterLink, RouterView } from 'vue-router'

export default {
  data() {
    return {
      formData: [],
      posts: [
        {
          title: 'Primeiro Post',
          datetime: Date.now(),
          content: 'Conteudo do post :)',

        },
        {
          title: 'Meu Segundo Post',
          datetime: Date.now(),
          content: 'Conteudo do segundo post :)',

        }
      ]
    }
  },
  methods: {
    submitForm(event) {
      event.preventDefault()

      this.posts.push(this.formData)
    },
    keyUpForm(event) {
      const inputName = event.target.name
      const inputValue = event.target.value

      this.formData[inputName] = inputValue
    }
  }
}

</script>

<template>
  <div id="lista-posts">
    <div class="post center" v-for="x in posts" :key="x.title">
      <h3>{{ x.title }}</h3>
      <h4>{{ x.datetime }}</h4>
      <p>{{ x.content }}</p>
    </div>
  </div>

  <form action="">
    <input name="title" placeholder="Título" @keyup="keyUpForm">
    <textarea name="content" id="" cols="30" rows="10" placeholder="Conteúdo" @keyup="keyUpForm"></textarea>

    <button type="submit" @click="submitForm">Submit</button>
  </form>



  <!--   <RouterView /> -->
</template>


<style>
form {
  width: 300px;
  display: flex;
  flex-direction: column;
}

#lista-posts {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}

.post {
  margin: 10px;
  background-color: lightgray;
  height: 200px;
  width: 300px;
}
</style>
