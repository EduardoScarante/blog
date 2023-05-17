<script>

export default {
  data() {
    return {
      formData: {},
      data: {}
    }
  },
  methods: {
    submitForm(event) {
      event.preventDefault()

      if (!this.formData.title || !this.formData.content) {
        alert("preencha os campos...")
        return
      }

      let now = new Date()
      let dataDaPostagem = `${now.getDate()}/${now.getMonth() + 1}/${now.getFullYear()}`

      /* PASSA OBJETO NO EVENTO */
      const obj = {
        title: this.formData.title,
        content: this.formData.content,
        datetime: dataDaPostagem
      }

      this.$emit("create-post", obj
      )

      alert(`Novo Post: 
      Titulo: ${obj.title}
      Mensagem: ${obj.content}` 
      )
      
      this.$router.push("/")
    },
  },
}
</script>


<template>
  <form id="form" action="">
    <input v-model="formData.title" placeholder="Título">
    <textarea v-model="formData.content" placeholder="Message"></textarea>

    <button type="submit" @click="submitForm">Criar</button>
  </form>
</template>

<style scoped></style>