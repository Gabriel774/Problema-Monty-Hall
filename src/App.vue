<template>
  <div id="app">
    <div>
      <h1 id="title">Problema de Monty Hall</h1>
    </div>
    <div v-if="!running">
      <p class="txt">
        Digite a quantidade de portas:
        <input type="number" v-model.number="quantity" />
      </p>
      <p class="txt">
        Qual a porta premiada? <input type="number" v-model.number="prize" />
      </p>
    </div>
    <p class="txt">
      <button @click="initRunning">
        {{ running ? "Reiniciar" : "Iniciar" }}
      </button>
    </p>
    <div v-if="running">
      <Doors :quantity="quantity" :prize="prize" />
    </div>
  </div>
</template>

<script>
import Doors from "./components/doors";
export default {
  name: "App",
  components: { Doors },
  data() {
    return {
      running: false,
      quantity: 2,
      prize: 1,
    };
  },
  methods: {
    initRunning() {
      if (this.running) this.running = !this.running;
      else {
        if (this.prize > this.quantity || this.prize <= 0) {
          alert("Erro: Porta inexistente");
        } else if (this.quantity <= 1) {
          alert("Erro: o jogo deve ter pelo menos duas portas");
        } else if (this.quantity > 50) {
          alert("Erro: o máximo de portas é 50");
        } else this.running = !this.running;
      }
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background: rgb(44, 62, 80);
  background: linear-gradient(
    90deg,
    rgba(44, 62, 80, 1) 0%,
    rgba(41, 128, 185, 1) 38%,
    rgba(39, 143, 174, 1) 94%
  );
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
#title {
  color: white;
  background: rgba(0, 0, 0, 0.377);
  border: solid 1px black;
  padding: 15px;
  text-align: center;
}
.txt {
  color: white;
  text-align: center;
}
</style>
