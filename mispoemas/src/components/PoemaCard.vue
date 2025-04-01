<template>
  <div class="poema-card">
    <div v-if="!isEditing">
      <h3>{{ poema.titulo }}</h3>
      <p>{{ poema.contenido }}</p>
      <button @click="isEditing = true">Editar</button>
      <button @click="$emit('eliminar', poema.id)">Eliminar</button>
    </div>
    <div v-else>
      <input v-model="editedPoema.titulo" placeholder="Título" />
      <textarea v-model="editedPoema.contenido" placeholder="Contenido"></textarea>
      <button @click="guardarCambios">Guardar</button>
      <button @click="isEditing = false">Cancelar</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    poema: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isEditing: false,
      editedPoema: { ...this.poema },
    };
  },
  methods: {
    guardarCambios() {
      this.$emit('editar', { id: this.poema.id, ...this.editedPoema });
      this.isEditing = false;
    },
  },
};
</script>

<style scoped>
.poema-card {
  background-color: rgba(255, 255, 255, 0.9);
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 15px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.poema-card:hover {
  transform: translateY(-5px);
}

.poema-card h3 {
  color: #00bcd4;
  margin-bottom: 10px;
}

.poema-card p {
  line-height: 1.6;
}

button {
    background-color: #00bcd4;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    margin: 7px;
  }
  
  button:hover {
    background-color: #0097a7;
  }
</style>