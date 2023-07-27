<template>
  <div class="about">
    <div class="container">
      <h1>Esta es una Página acerca de Cursos</h1>
      <div class="container">
        <div class="container" id="parrafo">
          <p> Esta modalidad es compatible con tu vida laboral y familiar.
              Dos sesiones a la semana</p>
              <p>Sesiones de dos horas</p>
              <p>Las sesiones se graban y te entregamos guías de repaso y profundización</p>
              <p>Desarrollo de ejercicios prácticos (más de 30 proyectos)</p>
              <p>Sesiones en vivo con profesores expertos</p>
              <p>1 semana de break después de cada módulo</p>
              <p>Cada módulo tiene una certificación</p>
              <p>Requiere de una dedicación de 12 horas semanales.</p>
        </div>
              <div id="carrusel">
            <b-carousel
            id="carousel-1"
            v-model="slide"
            :interval="4000"
            controls
            indicators
            background="#ababab"
            img-width="1024"
            img-height="480"
            style="text-shadow: 1px 1px 2px #333;"
            @sliding-start="onSlideStart"
            @sliding-end="onSlideEnd"
            >
            <!-- Text slides with image -->
           

            <!-- Slides with custom text -->
            <b-carousel-slide 
                class="d-block img-fluid w-100"
                width="1024"
                height="480"
                img-src="https://blog.back4app.com/wp-content/uploads/2021/05/Top-10-Front-End-Programming-Languages-1140x515.jpg">
                <h1>Hello world!</h1>
            </b-carousel-slide>

            <!-- Slides with image only -->
            <b-carousel-slide 
                class="d-block img-fluid w-100"
                width="1024"
                height="480"
                img-src="https://i0.wp.com/formaciononline.eu/wp-content/uploads/2018/04/cursos-desarrollador-front-end.jpg?w=640&ssl=1">

            </b-carousel-slide>

            <!-- Slides with img slot -->
            <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
            <b-carousel-slide>
                <template #img>
                <img
                    class="d-block img-fluid w-100"
                    width="1024"
                    height="480"
                    src="https://www.udalba.cl/blog/wp-content/uploads/2021/05/donde-estudiar-Desarrollo-Full-Stack-Rails.jpg"
                    alt="image slot">
                </template>
            </b-carousel-slide>

            <!-- Slide with blank fluid image to maintain slide aspect ratio -->
            <b-carousel-slide caption="Blank Image" img-blank img-alt="Blank image">
             
                <img
                    class="d-block img-fluid w-100"
                    width="1024"
                    height="480"
                    src="https://prod-discovery.edx-cdn.org/media/programs/card_images/2f377daa-30b3-487f-941c-18503633a4a1-12209ba765df.jpg"
                    alt="image slot"
                >
          >
            </b-carousel-slide>
            </b-carousel>
        </div>
      </div>
    </div>
   
  </div>
</template>
<script>
  export default {
    data() {
      return {
        slide: 0,
        sliding: null
      }
    },
    methods: {
      onSlideStart(slide) {
        this.sliding = true
      },
      onSlideEnd(slide) {
        this.sliding = false
      }
    }
  }
</script>
<style scoped>
#parrafo{
  width: 80%;
  color: cornsilk;
}
#carrusel{
  width: 90%;
  margin-left: 5%;
}
h1{
  background-color: plum;
}
p{
  background-color: mediumslateblue;
}
</style>
