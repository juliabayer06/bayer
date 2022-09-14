<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_livro: "",
      novo_autor: "",
      nova_editora: "",
      nova_categoria: "",
      livros: [
        {
          id: "ac803529-5e2d-45b2-a907-ca993bb301ea",
          livro: "É Assim que Acaba",
          autor: "Colleen Hoover",
          editora: "Galera",
          categoria: "Romance",
        },
        {
          id: "f0532191-04bb-44fe-be8b-8449ce321169",
          livro: "A garota do lago",
          autor: "Charlie Donlea",
          editora: "Faro Editorial",
          categoria: "Suspense",
        },
        {
          id: "29eaba8d-a376-485e-9509-5dddd6587f0d",
          livro: "Orgulho e preconceito",
          autor: "Jane Austen",
          editora: "Principis",
          categoria: "Romance",
        },
        {
          id: "d7c068f0-928f-4858-9ae3-eadc32edb230",
          livro: "Anjo da escuridão",
          autor: "Tilly Bagshawe",
          editora: "Record",
          categoria: "Terror",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_livro !== "") {
        const novo_id = uuid();
        this.livros.push({
          id: novo_id,
          nome: this.novo_livro,
          autor: this.novo_autor,
          editora: this.nova_editora,
          categoria: this.nova_categoria,
        });
        this.novo_livro = "";
        this.novo_autor = "";
        this.nova_editora = "";
        this.nova_categoria = "";
      }
    },
    excluir(livro) {
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
    },
    alerta() {
      alert("ok");
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerencimento de Livros</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_livro" placeholder="Nome do livro" />
      <input
        type="text"
        v-model="novo_livro"
        @keyup.enter="salvar"
        placeholder="Livros"
      />
      <input
        type="text"
        v-model="novo_autor"
        @keyup.enter="salvar"
        placeholder="Autores"
      />
      <input
        type="text"
        v-model="nova_editora"
        @keyup.enter="salvar"
        placeholder="Editoras"
      />
      <input
        type="text"
        v-model="nova_categoria"
        @keyup.enter="salvar"
        placeholder="Categorias"
      />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <td>ID</td>
            <td>Livros</td>
            <td>Autores</td>
            <td>Editoras</td>
            <td>Categorias</td>
            <td>Ações</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.nome_livro }}</td>
            <td>{{ livro.autor }}</td>
            <td>{{ livro.editora }}</td>
            <td>{{ livro.categoria }}</td>

            <td>
              <button class="botao" @click="alerta(livro)">Editar</button>
              <button class="botao" @click="excluir(livro)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style></style>
