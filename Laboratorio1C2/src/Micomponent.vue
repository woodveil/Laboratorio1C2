<template>
  <div id="app">
    <h1>Calculadora de Agua</h1>

    <form @submit.prevent="agregarConsumo">
      <label for="cantidad">Cantidad (ml):</label>
      <input v-model="cantidad" type="number" id="cantidad" />
      <button type="submit">Agregar</button>
    </form>

    <p v-if="total === 0">Aún no has registrado consumo.</p>
    <p v-else>Total consumido: {{ total }} ml</p>

    <ul>
      <li v-for="(registro, index) in registros" :key="index">
        {{ registro }} ml
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cantidad: "",
      registros: [],
      total: 0
    };
  },
  methods: {
    agregarConsumo() {
      if (this.cantidad.trim() === "" || this.cantidad <= 0) {
        alert("Ingresa una cantidad válida");
        return;
      }
      this.registros.push(this.cantidad);
      this.total += parseInt(this.cantidad);
      this.cantidad = "";
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  max-width: 400px;
  margin: auto;
  padding: 20px;
  background: #eafaf1;
  border-radius: 10px;
}

h1 {
  text-align: center;
  color: #2c3e50;
}

form {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}

input, button {
  padding: 8px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

button {
  background: #3498db;
  color: white;
  cursor: pointer;
}

button:hover {
  background: #2980b9;
}
</style>
