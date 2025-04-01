<template>
  <div id="app">
    <PoemasLista />
  </div>
</template>

<script>
import PoemasLista from './components/PoemasLista.vue';

export default {
  components: {
    PoemasLista,
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
  background: linear-gradient(135deg, #a8edea, #fed6e3);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #333;
}

#app {
  width: 80%;
  max-width: 800px;
  background-color: rgba(255, 255, 255, 0.8);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h2 {
  color: #8e44ad;
  text-align: center;
  margin-bottom: 20px;
}
</style>