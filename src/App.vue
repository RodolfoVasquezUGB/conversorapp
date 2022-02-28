<template>
  <div id="app">
   <Navbar @seleccionar-cantidad="cantidadSeleccionada=$event"/>  
   <ConversorUnidades v-bind:cantidadFisica="cantidadSeleccionada"/>
  </div> 
</template>


<script>
import Navbar from './components/Navbar.vue'           
import ConversorUnidades from './components/ConversorUnidades.vue'

export default {
  name: 'app',

  components: {  
    ConversorUnidades,
    Navbar
  },

  data: function(){
    return{
      cantidadSeleccionada: {name:"Tiempo",id:3, units:["Segundos","Minutos","Horas"]} //unidad de conversion por defecto cuando inicia el sitio
    }
  },

  methods:{
 
  },

  computed: {
    getMeasure(){
      return this.cantidades.find(x => x.name==this.cantidadSeleccionada);
    }
  }
}

</script>

<style>

 #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display:flex;
  background-color:#505c64;
}
</style>


