<script>
import CategoriasApi from "@/api/categorias.js";
const CategoriasApi = new CategoriasApi();
export default {
  data() {
    return {
      categoria: {},
      categorias: [],
    };
  },
  async created() {
    this.categorias = await CategoriasApi.buscarTodasAsCategorias();
  },
  methods: {
    async salvar() {
      if (this.categoria.id) {
        await CategoriasApi.atualizarCategoria(this.categoria);
      } else {
        await CategoriasApi.adicionarCategoria(this.categoria);
      }
      this.categorias = await CategoriasApi.buscarTodasAsCategorias();
      this.categoria = {};
    },
    async excluir(categoria) {
      await CategoriasApi.excluirCategoria(categoria.id);
      this.categorias = await CategoriasApi.buscarTodasAsCategorias();
    },
    editar(categoria) {
      Object.assign(this.categoria, categoria);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de categorias</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_categoria" @keyup.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
  </div>
  <div class="list-items">
    <table>
      <thead>
        <tr>
          <td>ID</td>
          <td>Nome</td>
          <td>Ações</td>
        </tr>
      </thead>

      <tbody>
        <tr v-for="categoria in categorias" :key="categoria.id">
          <td>{{ categoria.id }}</td>
          <td>{{ categoria.name }}</td>
          <td>
            <button @click="editar(categoria)">editar</button>
            <button @click="excluir(categoria)">excluir</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>

</style>