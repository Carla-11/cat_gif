<template>
  <div class="container">
    <h1 class="text-center my-5">Crea tu GIF_CAT</h1>
    <div class="p-5 bg-light">
      <form @submit.prevent="solicitarGato">
        <div class="form-group">
          <label for="titulo">Titulo: </label>
          <input type="text" class="form-control" v-model="titulo" />
        </div>

        <div class="form-group">
          <label for="color">Filtro</label>
          <select class="form-control" v-model="filtro">
            <option value="blur">BLur</option>
            <option value="mono">Mono</option>
            <option value="sepia">Sepia</option>
            <option value="negative">Negative</option>
            <option value="paint">Paint</option>
            <option value="pixel">Pixel</option>
          </select>
        </div>

        <div class="form-group bloque">
          <label for="color">Color</label>
          <select class="form-control colores" v-model="color">
            <option value="white">Blanco</option>
            <option value="green">Verde</option>
            <option value="red">Rojo</option>
            <option value="blue">Azul</option>
            <option value="yellow">Amarillo</option>
          </select>
        </div>
         <span class="circulo" :style="{color: color}"></span>
        <div class="form-group">
          <label for="exampleInputEmail1">tamaño </label>
          <input type="text" class="form-control" v-model="tamano" />
        </div>
        <button type="submit" class="btn btn-primary">Crear</button>
      </form>
    </div>
    <hr />
    <div class="p-5 bg-light border w-100" v-if="url">
      <h3 class="text-center"><em>Tu gato es</em></h3>
      <img :src="url" alt="gato" class="img-fluid" />
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: ["url"],
  data() {
    return {
      titulo: "",
      color: "",
      tamano: "",
      filtro: "",
    };
  },
  methods: {
    solicitarGato() {
      if (this.titulo && this.color && this.tamano && this.filtro) {
        let solicitud = {
          titulo: this.titulo,
          color: this.color,
          tamano: this.tamano,
          filtro: this.filtro,
        };
        this.$emit("solicitandoGato", solicitud);
      } else {
        console.log("nose puede realizar gato");
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.circulo{
  width: 50px;
  height: 50px;
  display: inline-block;
  border-radius: 50%;
  border: 1px solid black;
  margin-left: 40px;
  
}
.colores{
  width: 400px;
}

.bloque{
  display: inline-block;
}
</style>
