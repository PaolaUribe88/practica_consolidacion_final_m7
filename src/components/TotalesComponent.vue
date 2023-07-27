<template>
    <div id="TotalesComponent" class="container">
        <div class="container" id="contenedor">
            <div id="totalCupos" class="container">
                <p><i class="fa-solid fa-user-group"></i>Cantidad total de alumnos permitidos: {{totalCupos}} alumnos</p>
            </div><br>
            <div id="totalInscritos" class="container">
                <p><i class="fa-solid fa-user-check"></i> Cantidad total de alumnos inscritos: {{totalInscritos}} alumnos</p>
            </div><br>
            <div id="totalCuposRestantes" class="container">
                <p><i class="fa-solid fa-user-plus"></i> Cantidad total de cupos restantes: {{totalRestantes}} alumnos</p>
            </div><br>
            <div id="totalCursosTerminados" class="container">
                <p><i class="fa-solid fa-ban"></i> Cantidad total de cursos terminados: {{totalTerminados}} cursos</p>
            </div><br>
            <div id="totalCursosActivos" class="container">
                <p><i class="fa-sharp fa-solid fa-bell"></i> Cantidad total de cursos Activos: {{totalActivos}} cursos</p>
            </div><br>
            <div id="totalCursos" class="container">
                <p><i class="fa-sharp fa-solid fa-bell"></i> Cantidad total de cursos: {{totalCursos}} cursos</p>
            </div><br>
        </div>
    </div>        
  </template>
  
  <script>
  import { mapState,mapActions } from 'vuex';
  export default {
    name: 'TotalesComponent',
    props: {
    },
    data:function(){
      return{
      }
    },
    methods:{
      ...mapActions('informacion_curso',['consultarDatosTabla']),
    },
    computed:{
      ...mapState('informacion_curso',['datos_tabla']),
      totalCupos: function(){
        let valorInicial =0;
        let total = this.datos_tabla.reduce( (acumulador, registro) => acumulador + registro.cupos, valorInicial);
        return total;
      },
      totalInscritos: function(){
        let valorInicial =0;
        let total = this.datos_tabla.reduce( (acumulador, registro) => acumulador + registro.inscritos, valorInicial);
        return total;
      },
      totalRestantes: function(){
        let valorInicial =0;
        let totalCupos = this.datos_tabla.reduce( (acumulador, registro) => acumulador + registro.cupos, valorInicial);
        let totalInscritos = this.datos_tabla.reduce( (acumulador, registro) => acumulador + registro.inscritos, valorInicial);
        let diferencia = totalCupos - totalInscritos;
        return diferencia;
      },
      totalTerminados: function(){
        let valorInicial =0;
        let totalTerminados = 0;
            totalTerminados = this.datos_tabla.reduce( (acumulador, registro) => {
                if(registro.terminado == true)
                {
                    acumulador++;
                }
                return acumulador;
            } , valorInicial);
            return totalTerminados;
      },
      totalActivos: function(){
        let valorInicial =0;
        let totalActivos = 0;
        let longitud = this.datos_tabla.length;
        for(let i=0; i < longitud ; i++){
            if(this.datos_tabla[i].terminado == false){
                totalActivos++;
            }
        }
            return totalActivos;
      },
      totalCursos: function(){
        let totalC = this.datos_tabla.length;
            return totalC;
      },
    },
    watch:{},
    created(){
        // this.consultarCursos();
        // this.consultarDatosTabla();
    }
  }
  </script>
  <style scoped>
 #totalCupos{
    border: solid 1px blueviolet;
    color:blueviolet;
    text-align: start;   
}
#totalInscritos{
    border: solid 1px rgb(26, 86, 196);
    color:rgb(26, 86, 196);
    text-align: start;
}
#totalCuposRestantes{
    border: solid 1px red;
    color:red;
    text-align: start;
}
#totalCursosTerminados{
    border: solid 1px rgb(196, 13, 196);
    color:rgb(196, 13, 196);
    text-align: start;
}
#totalCursosActivos{
    border: solid 1px olive;
    color:olive;
    text-align: start;
}
#totalCursos{
    border: solid 1px orange;
    color:orange;
    text-align: start;
}
  </style>
  