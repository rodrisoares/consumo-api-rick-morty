<template>
  <div id="app">
    <Search @search="search" />
    <ul>
      <CharacterCard v-for="personagem of personagens" :key="personagem.id" :personagem="personagem" @exibir-detalhes="exibirDetalhes" />
    </ul>
  </div>
</template>

<script>
import CharacterCard from './components/CharacterCard.vue';
import Search from './components/Search.vue';

export default {
  name: 'App',
  components: {
    CharacterCard,
    Search
  },
  data() {
    return {
      personagens: [{isSelected: false}],
      url: "https://rickandmortyapi.com/api/character",
      exibirBotao: true,
    };
  },
  mounted() {
    fetch(this.url)
      .then((response) => response.json())
      .then((data) => (this.personagens = data.results));
  },
  methods: {
    search(name) {
      fetch(`${this.url}?name=${name}`)
        .then((response) => response.json())
        .then((data) => {
          if (!data.results) {
            alert("Nenhum personagem encontrado.");
          } else {
            this.personagens = data.results;
          }
        }) 
    },
    exibirDetalhes(persId){
      this.personagens = this.personagens.map(personagem => {
        if (personagem.id === persId) {
          return {
            ...personagem,
            isSelected: !personagem.isSelected,
          }
        } else return personagem;
      })
    }
  }
}
</script>