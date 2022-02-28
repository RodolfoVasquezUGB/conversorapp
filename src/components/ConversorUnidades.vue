<template>
  <div id="container">

    <h1>{{cantidadFisica.name}}</h1>

    <div id="main">
        <input type="text" v-model="fromValue" placeholder="Ingresar la cantidad">
        <select v-model="fromUnit">
            <option v-for="unit in cantidadFisica.units" v-bind:key="unit"> {{unit}} </option>
        </select>
        <img src="https://icones.pro/wp-content/uploads/2021/06/symbole-fleche-droite-orange.png" width="50" height="50" viewBox="0 0 24 24" fill="rgb(77, 186, 135)">
        <p id="result">
            {{result}}
        </p> 
        <select v-model="resultUnit" placeholder="result">
            <option v-for="unit in cantidadFisica.units" v-bind:key="unit"> {{unit}} </option>
        </select>
    </div>
    <h2>El resultado de la conversión es: {{result}} {{resultUnit}}</h2>
    
    <img id="imagen" src="https://i.ytimg.com/vi/nqxHnu4LJ6k/maxresdefault.jpg" width="1300" height="500">
  </div>
</template>

<script>
export default {
  name: 'Converter',
  props: {
    cantidadFisica: Object  
  },
  data: function(){           
       return{
         fromValue:1,
         fromUnit:"",
         resultUnit:""
       }
  },
  methods:{
      toMinutes: function(value,fromUnit, resultUnit){   
        if(fromUnit=="Segundos" && resultUnit=="Segundos"){
             return value;
         } else if (fromUnit=="Segundos" && resultUnit =="Minutos"){
             return value/60;
         } else if (fromUnit=="Segundos" && resultUnit =="Horas"){
             return value/3600;
         } else if (fromUnit=="Minutos" && resultUnit =="Minutos"){
             return value;
         } else if (fromUnit=="Minutos" && resultUnit =="Segundos"){
             return value*60;
         } else if (fromUnit=="Minutos" && resultUnit =="Horas"){
             return value/60;
         } else if (fromUnit=="Horas" && resultUnit =="Horas"){
             return value;
         } else if (fromUnit=="Horas" && resultUnit =="Segundos"){
             return value*3600;
         } else if (fromUnit=="Horas" && resultUnit =="Minutos"){
             return value*60;    
        }
      }
  },


  computed: {           
      result: function(){
            let value = parseFloat(this.fromValue);  
            if(isFinite(value)){                     

              switch(this.cantidadFisica.name){    
                case("Tiempo"): {
                        let valueInMinutes = this.toMinutes(value,this.fromUnit,this.resultUnit);
                        switch(this.resultUnit){
                        case("Segundos"):
                            return parseFloat((valueInMinutes).toFixed(5));   
                        case("Minutos"):
                            return parseFloat((valueInMinutes).toFixed(5));
                        case("Horas"):
                            return parseFloat((valueInMinutes).toFixed(5));
                        default:
                            console.log("Error detectado - unidad no seleccionada");
                            return "...";
                        }
                }
              }
            }      
            return "...";  
      }
  }
}
</script>

<style scoped>
  #container{
    width:80vw;
    color:rgb(20,20,20);
    height:100vh;
    display:flex;
    flex-direction:column;
    justify-content:flex-start;
  }
  h1{
    width:100%;
    background-color:#73848f;
    box-sizing:border-box;
    padding:40px;
    color: rgb(255, 255, 255);
  }

  h2{
    width:100%;
    background-color:#73848f;
    box-sizing:border-box;
    padding:10px;
    color: rgb(255, 255, 255);
  }

  #main{
    display:flex;
    box-sizing:border-box;
    padding:40px;
    padding-left: 300px;
  }
  
  #main>*{
    margin:0 5px 0 5px;
  }
  input,select{
    padding:10px;
    border: 2px solid rgb(223, 113, 62);
    border-radius:10px;
    width:10vw;
    font-family:"Source Sans Pro";
    font-size:1em;
    display:flex;
    align-items:center;
  }
  #result{
    padding:10px;
    border: 2px solid rgb(223, 113, 62);
    border-radius:10px;
    width:10vw;
    font-family:"Source Sans Pro";
    font-size:1em;
    display:flex;
    align-items:center;
    background-color: white;
  }
  #imagen{
    box-sizing:border-box;
    display: block;   
    margin: auto;
    }
</style>