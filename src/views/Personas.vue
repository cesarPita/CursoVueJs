<template>
 <!--aqui todo el codigo html-->
  <div>
    <h1>Lista de Personas</h1>

    Nombre: <input type="text" v-model="nombre">
    <br>
    Hola como estas :  {{nombre}}
    <hr>
    N1: <input type="text" v-model="n1"><br>
    N2: <input type="text" v-model="n2"><br>
    <!--<button v-on:click="producto()">Multiplicar</button><br>-->
    <button @click="producto">Multiplicar</button><br>
    La suma es: {{sumar}} <br>
    La multiplicacion es: {{multiplicar}}
    <hr>
    <h3>LISTA DE PERSONAS</h3>
    <input type="text" v-model="txtBuscar"><br>
    <table border="1" width="100%">
      <tr>
      <th>Nombre</th>
      <th>Edad</th>
      <th>Licencia</th>
      </tr>
      <tr v-for="(row, index) in buscarPersonas" :key="index">
        <td>{{row.nombre}}</td>
        <td>{{row.edad}}</td>
        <td>
          <strong v-if="row.licencia_conducir === true">SI</strong>
          <strong v-else>NO</strong>
        </td>
      </tr>
    </table>
  </div>

</template>
<!-- aqui va el codigo java script o vuejs-->
<script>

export default {
  name: "Personas",

  data:() =>({
  //permite declarar variables locales
    nombre:"",
    n1:1,
    n2:0,
    multiplicar:0,
    txtBuscar:"",
    persona:[
     {"nombre":"Cesar", "edad":15, "licencia_conducir":true},
      {"nombre":"Juan", "edad":5, "licencia_conducir":false},
      {"nombre":"Luis", "edad":45, "licencia_conducir":true},
      {"nombre":"Ivan", "edad":45, "licencia_conducir":false}
      ]
  }),
  computed:{
    //cambiar el estado o el valor de las variables en tiempo de ejecucion, operaciones de variables
    sumar(){
      return parseInt(this.n1) + parseInt(this.n2);
    },
    buscarPersonas(){
      return this.persona.filter(item=>{
        return item.nombre.includes(this.txtBuscar);
      })
    }
  },
  created(){
  //se ejecuta antes de dibujar el DOM de la pagina
  },
  mounted() {
    //despues de dibujar ek DOM de la página
  },
  methods:{
    //todos los metodos o funciones del componente
    producto()
    {
      this.multiplicar = parseInt(this.n1) * parseInt(this.n2);
    }
  }
}
</script>
<!-- aqui va el codigo de estilos css para la vista o componente-->
<style scoped>

</style>