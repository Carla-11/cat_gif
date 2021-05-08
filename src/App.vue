<template>
  <div id="app">

  <RandomCat  @solicitandoGato="conexionApi"  :url="url"/>
    
  </div>
</template>

<script>
import RandomCat from './components/RandomCat.vue'

export default {
  name: 'App',
  data() {
    return {
      url: ''
    }
  },
  components: {
    RandomCat
  },
  methods: {
    conexionApi(solicitud){
      fetch(`https://cataas.com/cat/gif/says/${solicitud.titulo}?filter=${solicitud.filtro}&color=${solicitud.color}&size=${solicitud.tamano}`)
      .then(resp => {
        console.log(resp);
        this.url= resp.url;
      })
      .catch(error => console.error(error));

    }
  },
}
</script>

<style>

</style>
