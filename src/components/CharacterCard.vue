<template>
    <div class="card mb-4 mx-2" style="width:400px;">
      <img :src="personagem.image" alt="imagem personagem"><br>  
      <div class="title"> Nome:  
        <span class="fw-bold"> {{ personagem.name }} </span>
      </div> <br>
      <div v-if="!personagem.isSelected" >
        <b-button class="btn-exbir-detalhes" variant="success" @click="exibirDetalhes(personagem.id)">Exibir detalhes</b-button>
      </div>
      <div>
        <div v-if="personagem.isSelected" class="card-body">
          <div class="card-body list-group-item-success">
            <div class="list-group">   
              <div class="card-title">Espécie: <span class="fw-bold">{{ personagem.species }}</span></div>
              <div class="card-title">Status: <span class="fw-bold">{{ personagem.status  }}</span></div>
              <div class="card-title">Gênero: <span class="fw-bold">{{ personagem.gender  }}</span></div>
              <div class="card-title">Origem: <span class="fw-bold">{{ personagem.origin.name }}</span></div>
              <div class="card-title">Local: <span class="fw-bold">{{ personagem.location.name }}</span></div>
            </div>
          </div>                           
          <b-button class="btn-esconder-detalhes" variant="success" @click="exibirDetalhes(personagem.id)">Esconder detalhes</b-button>     
        </div> 
      </div>
    </div>
</template>
  
<script>
  export default {
    name: 'Card',
    props: {
      personagem: Object
    },
    methods: {
      exibirDetalhes(persId){
        this.$emit('exibir-detalhes', persId);
      }
    }
  }
</script>
<style>
  body {
      display: flex;
      justify-content: center;
      align-items: center;
  }
  ul {
      display: flex;
      flex-direction: row;
      align-content: center;
      align-items: flex-start;
      justify-content: space-around;
      flex-wrap: wrap;
  }
  img {
      width: 100%;
      height: auto;
  }
  .title {
      margin-top: 10px;
      position: relative;
      left: 20px;
  }
  .card-body {
      padding:10px;
      margin: 10 0 20;
  }
  .btn-exbir-detalhes {
      position: relative;
      left: 10px;
      margin: 10px;
  }
  .btn-esconder-detalhes {
      position: relative;
      left: -20px;
      margin: 20px;
  }
</style>
  