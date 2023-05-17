<script>
export default {
  data() {
    return {
      titleSearch: ''
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
  }
}

</script>

<template>
  <div class="container">
    <div id="searchBox">
      <input id="searchInput" type="text" v-model="titleSearch" placeholder="Procure pelo título do Post...">
    </div>

    <div id="lista-posts">
      <div class="post center" v-for="x in 
                filteredPost" :key="x.title">
        <div>
          <h3>{{ x.title }}</h3>
          <p>{{ x.content }}</p>
        </div>
        <h4><i>{{ x.datetime }}</i></h4>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container{
  width: 100vw;
}

#searchInput {
  background-color: white;
  box-shadow: 3px 3px 15px lightgray;
  border: none;

  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;

  width: 500px;
  padding: 10px;
  margin-top: 5px;

  border: 3px;
}

#searchBox {
  text-align: center;

  padding-top: 10px;
}

#lista-posts {
  width: 100%;
  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  justify-content: center;

}

.post {
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  background-color: white;

  height: 200px;
  width: 270px;

  box-shadow: 4px 4px 15px lightgray;

  border-radius: 10px;
  padding: 10px;
  margin: 10px;
}

.post h4 {
  font-weight: 100;
  color: #535353;

  text-align: end;
}

@media (max-width: 600px) {

  form>*,
  #searchInput {
    width: 100vw;
  }

  .post {
    width: 100vw;
  }
}
</style>
