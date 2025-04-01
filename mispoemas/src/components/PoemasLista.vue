<template>
    <div>
      <h2>Mis Poemas</h2>
      <div v-for="poema in poemas" :key="poema.id">
        <PoemaCard :poema="poema" @editar="actualizarPoema" @eliminar="eliminarPoema" />
      </div>
      <h3>Agregar Nuevo Poema</h3>
      <input v-model="nuevoPoema.titulo" placeholder="Título" />
      <textarea v-model="nuevoPoema.contenido" placeholder="Contenido"></textarea>
      <button  @click="agregarPoema">Agregar</button>
    </div>
  </template>
  
  <script>
  import PoemaCard from './PoemaCard.vue';
  
  export default {
    components: {
      PoemaCard,
    },
    data() {
      return {
        poemas: [
          
        ],
        nuevoPoema: {
          titulo: '',
          contenido: '',
        },
        nextPoemaId: 3,
      };
    },
    methods: {
      agregarPoema() {
        this.poemas.push({
          id: this.nextPoemaId++,
          ...this.nuevoPoema,
        });
        this.nuevoPoema.titulo = '';
        this.nuevoPoema.contenido = '';
      },
      eliminarPoema(id) {
        this.poemas = this.poemas.filter((poema) => poema.id !== id);
      },
      actualizarPoema(poemaActualizado) {
        const index = this.poemas.findIndex((poema) => poema.id === poemaActualizado.id);
        if (index !== -1) {
          this.poemas.splice(index, 1, poemaActualizado);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  h3 {
    color: #8e44ad;
    margin-top: 20px;
  }
  
  input,
  textarea {
    width: calc(100% - 22px);
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-sizing: border-box;
  }
  
  button {
    background-color: #00bcd4;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #0097a7;
  }
  </style>