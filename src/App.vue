<template>
  <div id="app">
    <nav>
      <div>
        <b-navbar toggleable="lg" type="dark" id="barraNav">
          <b-navbar-brand href="#">CURSOS ALFAWEB</b-navbar-brand>
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
          <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
              <b-nav-item href="#"><router-link to="/about">About</router-link></b-nav-item>
              <b-nav-item href="#"><router-link to="/"><i class="fa-solid fa-house"></i></router-link></b-nav-item>
              <b-nav-item href="#"><router-link to="/administracion"><i class="fa-solid fa-screwdriver-wrench"></i></router-link></b-nav-item>
            </b-navbar-nav>
            <!-- Right aligned nav items -->
            
              <!-- <b-nav-form>
                <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
                <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
              </b-nav-form> -->
          </b-collapse>
        </b-navbar>
      </div>      
    </nav>
    <router-view/>
  </div>
</template>
<script>
import { mapActions } from 'vuex';

/*@import "https://use.fontawesome.com/releases/v5.2.0/css/all.css";*/
export default{
  name:'App',
  data: function(){
    return{

    }
  },
  props:{

  },
  components:{
    
  },
  methods:{
    //mapea sobre el modulo(informacion_curso) el accion (consultarCursos)
    ...mapActions('informacion_curso',['consultarCursos', 'consultarDatosTabla']),
  },
  computed:{

  },
  watch:{

  },
  beforeMount(){
    this.consultarCursos();
    this.consultarDatosTabla();
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
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
#barraNav{
  background-color: blueviolet;
}
</style>
