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

        },
        {
          title: 'Meu Segundo Post',
          content: 'Conteudo do segundo post :)',

        }
      ]
    }
  },
  methods: {
    submitForm(event) {
      event.preventDefault()


      //this.posts.push({ ...this.formData })

      //Para resetar o valor dos formulários 
      //document.getElementById("form").reset()
      //retirar o @value do form

      let now = new Date()
      let dataDaPostagem = `${now.getDate()}/${now.getMonth() + 1}/${now.getFullYear()}`

      this.posts.push({
        title: this.formData.title,
        content: this.formData.content,
        datetime: dataDaPostagem
      })

      this.formData = {}

    },
    keyUpForm(event) {
      //const inputName = event.target.name
      //const inputValue = event.target.value
      //this.formData[inputName] = inputValue

      // Conceito de descontruir objeto
      /*    const { name, value } = event.target
            this.formData[name] = value */
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


  <form id="form" action="">
    <!--     <input 
      name="title" 
      placeholder="Título" 
      @keyup="keyUpForm"
      :value="formData.title"
      > -->

    <!--     <textarea 
      name="content" 
      id="" 
      cols="30" 
      rows="10" 
      placeholder="Conteúdo" 
      @keyup="keyUpForm"
      :value="formData.content"
      ></textarea> -->

    <!-- Conceito de v-model, faz a ligação com o objeto formData no objeto title - conceito de two way data-binding -->

    <input v-model="formData.title" placeholder="Título">
    <textarea v-model="formData.content" placeholder="Message"></textarea>

    <button type="submit" @click="submitForm">Submit</button>
  </form>



  <!--   <RouterView /> -->
</template>


<style>
form {
  width: 99vw;
  display: flex;
  flex-direction: column;
  align-items: center;

  position: absolute;
  bottom: 5px;
}

form > *{
  background-color: white;
  box-shadow: 3px 3px 15px lightgray;
  border: none;

  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  
  width: 500px;
  padding: 10px;
  margin-top: 5px;

  border: 3px;
}

form button{
  background-color: rgb(53, 53, 53);
  color: whitesmoke;
  font-weight: 800;
  width: 100px;
  border-radius: 10px
}

#lista-posts {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}

.post {
  margin: 10px;
  background-color: white;
  height: 200px;
  width: 300px;

  box-shadow: 4px 4px 15px lightgray;

  border-radius: 10px;
  padding: 10px;
}
</style>
