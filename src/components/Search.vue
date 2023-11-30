<template>
    <div class="buscar-container">
      <div class="img-container">
        <img src="@/assets/img/rickandmorty.png" alt="logo rick and morty"/>
      </div>
      <div>
        <div id="form">
          <b-form-input class="mt-4" type="text" v-model="name"  placeholder="Pesquise um personagem"/>    
          <b-button variant="outline-primary" class=" mt-2" v-on:click="search">Buscar</b-button>
        </div>
      </div>
    </div>
</template>
  
<script>
  export default {
    name: 'Search',
    data() {
      return {
        name: ""
      };
    },
    methods: {
      search() {
        this.$emit('search', this.name);
        if(this.name){
          this.name = "";
        } else {
          alert("Digite o nome do personagem!")
        }
      }
    }
  }
</script>
<style>
    #form {
        position: absolute;
        right: -80px;
        top: 80px;
        width: 20%;
        padding: 20px;
    }
    .buscar-container {
        position: relative;
        right:6%; 
    }
    .img-container {
      width: 25%;
      position: relative;
      left:10%; 
      height: auto;
    }
</style>