<script>
import axios from "axios";

export default{
  data () {
    return {
      jogadores: [],
      times: [],
      jogador: {},
    };
  },
  async created() {
    await this.buscarTodosOsJogadores();
    await this.buscarTodosOsTimes();
  },
  methods: {
    async buscarTodosOsTimes(){
      const times = await axios.get("http://localhost:4000/times");
      this.times = times.data;
    },
    async buscarTodosOsJogadores(){
      const jogadores = await axios.get("http://localhost:4000/jogadores?expand=time");
      this.jogadores = jogadores.data;
    },
    async salvar(){
      await axios.post("http://localhost:4000/jogadores", this.jogador)
      await this.buscarTodosOsJogadores();
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de jogadores</h2>
    </div>
  </div>
  <div class="form-input">
    <input type="text" v-model="jogador.nome" placeholder="Nome" />
    <input type="text" v-model="jogador.anoNascimento" placeholder="Idade" />
    <input type="text" v-model="jogador.peso" placeholder="Peso" />
    <input type="text" v-model="jogador.altura" placeholder="Altura" />
    <input type="text" v-model="jogador.funcao" placeholder="Função de campo" />
    <select v-model="jogador.timeId">
    <option v-for="time in times" :key="time.id" :value="time.id">
     {{ time.nome }}
    </option>
    </select>
    <button @click="salvar">Salvar</button>
  </div>
  <div class="list-items">
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Nome</th>
          <th>Idade</th>
          <th>Peso</th>
          <th>Altura</th>
          <th>Time</th>
          <th>Função</th>
          <th>Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="jogador in jogadores" :key="jogador.id">
          <td>{{ jogador.id }}</td>
          <td>{{ jogador.name }}</td>
          <td>{{ 2022 - jogador.anoNascimento}}Anos</td>
          <td>{{ jogador.peso }}</td>
          <td>{{ jogador.altura }}</td>
          <td>{{ jogador.timeId }}</td>
          <td>{{ jogador.funcao }}</td>
          <td>???</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
