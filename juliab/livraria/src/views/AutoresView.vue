<script>
  import AutoresApi from "@/api/autores.js";
  const AutoresApi = new AutoresApi();
  export default {
    data() {
    return {
      autor: {},
      autores: [],
    };
  },
  async created() {
    this.autores = await AutoresApi.buscarTodosOsAutores();
  },
  methods: {
    async salvar() {
      if (this.autores.id) {
        await AutoresApi.atualizarAutor(this.autor);
      } else {
        await AutoresApi.adicionarAutor(this.autor);
      }
      this.autor = await AutoresApi.buscarTodosOsAutores();
      this.autor = {};
    },
    async excluir(autor) {
      await AutoresApi.excluirAutor(autor.id);
      this.autores = await AutoresApi.buscarTodosOsAutores();
    },
    editar(autor) {
      Object.assign(this.autor, autor);
    },
  },
};
</script> 

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de autores</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_autor" @keyup.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
  </div>
  <div class="list-items">
    <table>
      <thead>
        <tr>
          <td>ID</td>
          <td>Nome</td>
          <td>Sites</td>
          <td>Ações</td>
        </tr>
      </thead>

      <tbody>
        <tr v-for="autor in autores" :key="autor.id">
          <td>{{ autor.id }}</td>
          <td>{{ autor.name }}</td>
          <td>{{ autor.site }}</td>
          <td>
            <button @click="editar(autor)">editar</button>
            <button @click="excluir(autor)">excluir</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>

</style>
