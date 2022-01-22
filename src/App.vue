<template>
  <div class="container">
    <h2>{{titulo}}</h2>
    <hr>
    <div class="input-group">
      <input v-model="novaTarefa" @keyup.enter="adicionarTarefa" type="text">
      <span class="input-group-btn">
        <button class="btn btn-primary" @click="adicionarTarefa">Adicionar</button>
      </span>
    </div>

  <ul>
    <li v-for="tarefa, index in tarefas" :key="index">
      <input type="checkbox" v-model="tarefa.checked">
      <label :class="{checked: tarefa.checked}">{{tarefa.titulo}}</label>
    </li>
  </ul>

    <footer>
      <hr>
    <em>Altere Aqui o Nome da Sua Lista de Tarefas</em>
    <input type="text" v-model="titulo">
  </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      titulo:"Minha Lista de Tarefas",
      tarefas: [
        {titulo: "Estudar", checked: false},
        {titulo: "Ler", checked: true},
      ],
      novaTarefa: ""
    }
  },
  methods: {
    adicionarTarefa() {
      this.tarefas.push({
        titulo: this.novaTarefa,
        checked: false,
      })
      this.novaTarefa=""
    },
  }
}
</script>

<style>
.container {
  width: 40%;
  margin: 20px auto 10px auto;
}

ul li {
  list-style: none;
}

.checked {
  color: gray;
  text-decoration: line-through;
}
</style>

