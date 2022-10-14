<template>
    <h3 class="text-center">Progreso: {{porcentaje}}%</h3>
          <div class="progress">
              <div class="progress-bar progress-bar-striped progress-bar-animated bg-success"
              role="progressbar"
              :aria-valuenow="porcentaje" 
              aria-valuemin="0" 
              aria-valuemax="100" 
              :style="`with: ${porcentaje}%`" 
              ></div>
            </div>
            <h1> {{porcentaje}}</h1>
      

</template>

<script>
  export default {
      props: {
          porcentaje: Number,
      },
  };

</script>