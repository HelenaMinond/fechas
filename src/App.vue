<template>
  <div>
    <h1 class="my-5">Cuenta regresiva</h1>

    <h2>{{ tiempoInicial }} seg</h2>

    <button
      class="mx-3 mt-4 px-2"
      v-for="boton in arrBotones"
      :key="boton.name"
      @click="start(boton.valor)"
    >
      {{ boton.name }}
    </button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      arrBotones: [
        { name: "3s", valor: 3 },
        { name: "1m", valor: 60 },
        { name: "5m", valor: 300 },
        { name: "10m", valor: 600 },
        { name: "30m", valor: 1800 },
      ],
      tiempoInicial: "0000",
      tiempoFinal: "",
      tiempo: "",
    };
  },
  methods: {
    start(val) {
      this.tiempoInicial = val;
      this.tiempoFinal = this.tiempoInicial - val;

      this.tiempo = setInterval(() => {
        this.tiempoInicial--;
        if (this.tiempoInicial == this.tiempoFinal) {
          clearInterval(this.tiempo);
        }
      }, 1000);
    },
  },
};
</script>

<style lang="scss">
div {
  text-align: center;
}

h1,
h2 {
  font-weight: 700;
}

h2 {
  color: rgb(170, 169, 169);
}

button {
  border: 0px;
  background: rgb(206, 206, 206);
}

button:hover {
  border: solid 3px rgb(91, 186, 218);
  border-radius: 5px;
}
</style>
