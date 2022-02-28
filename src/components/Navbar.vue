<template>
 <div id="nav">
     <div id="header">
         <img src="https://logos-marcas.com/wp-content/uploads/2021/02/Sky-Logo.png" height="40" width="60">
         Conversor de Unidades
    </div>
     <a v-for="cantidad in cantidades" v-bind:key="cantidad.name" @click="$emit('seleccionar-cantidad',cantidad)" >
        {{cantidad.name}}
     </a>
     <div id="footer">
        Realizado por:
        <li>Jose Rodolfo </li>
        <li>Rodolfo Murillo</li>
        <li>Katya Viscarra </li>
     </div>
 </div>
</template>


<script>
export default {
  name:'Navbar',
  data: function(){
      return{
          cantidades: [  //Aqui se encuentran todas las unidades a utilizar con sus conversiones
           {name:"Longitud",id:0, units:[""]},
           {name:"Monedas",id:1, units:[""]},
           {name:"Masa",id:2, units:[""]},
           {name:"Tiempo",id:3, units:["Segundos","Minutos","Horas"]},
           {name:"Almacenamiento",id:4, units:[""]}
          ]
      }
  },
  methods:{

  }
}
</script>


<style scoped>
    #nav{
        display:flex;
        flex-direction:column;
        height:100vh;
        width:20vw;
        background-color:#73848f;
        color:white;
    }

    #nav>div{
        display:flex;
        flex-direction:column;
        justify-content:center;
        align-items:center;
        padding:35px 0 30px 0;
        text-align:Center;
        vertical-align:middle;
    }

    #header{
       background-color:#505c64;
       padding:10px;
    }

    a{
       text-align:center;
       padding:35px;
       background-color:rgb(223, 113, 62);
       transition:background-color 0.5s;
       cursor:pointer;
    }
    a:hover{
        background-color:rgb(223, 113, 62);
    }

    #footer{
        height:15vh;
        background-color:#505c64;
        margin-top:auto;
        box-sizing:border-box;
        padding:15px;
        font-size:0.8em;
    }
</style>