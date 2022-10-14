<template>

    <div class="row">
        <h3 class="text-center">Progreso: 0%</h3>
          <div class="progress">
              <div class="progress-bar progress-bar-striped progress-bar-animated bg-success"
              role="progressbar"
              :aria-valuenow="75" 
              aria-valuemin="0" 
              aria-valuemax="100" 
              :style="with: 100%" 
              ></div>
            </div>
    


        <div class="col-12 mb-4">
            <ProgressBar :porcentaje="porcentaje">

            </ProgressBar>
            
        </div>


        <div class="col-12 col-md-5">
            <form @submit.prevent="registrarproyecto">
                <div class="mb-3">
                <label  class="form-label">Proyecto</label>
                <input v-model.trim="proyecto" type="text" class="form-control" required />
                </div>

        <div class="mb-3">
            <label  class="form-label">Actividad</label>
            <select v-model="tipo" class="form-select" required>
            <option disabled selected value="">Selecciona un tipo de actividad</option>
            <option>Aplicaciones Wen con Vue.js</option>
            <option>Backend Services con Node.js</option>
            <option>App móvil con React Native</option>
        </select>
      </div>

      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-check-label">Urgente</label>
        <input v-model="urgente" type="checkbox" class="form-check-input"/>
      </div>


      <button type="submit" class="btn btn-primary">Guardar</button>
    </form>
        </div>

        <div class="col-12 col-md-7">
            <total-proyectos :numeroProyectos="numeroProyectos" :proyectos="proyectos" :cambiarEstado="cambiarEstado" :limpiarData="limpiarData" :borrado="borrado"/>

        </div>
        
    </div>
    
</template>

<script>

    export default{
        data: () => ({
                proyecto: "",
                tipo: "",
                urgente: false,
                proyectos: [],
                numeroProyectos: 0,
                
            }),
            methods: {
                registrarproyecto() {
                    const proyecto = {
                        proyecto: this.proyecto,
                        tipo: this.tipo,
                        urgente: this.urgente,
                        completado: false,
                    };
                    this.proyectos.push(proyecto);

                    this.numeroProyectos++;
                    this.proyecto = "",
                    this.tipo = "",
                    this.urgente = false;
                
            },
            cambiarEstado(proyecto,campo) {
                //this.proyectos[id].urgente = !this.proyectos[id].urgente;
                proyecto[campo] = !proyecto[campo];

                this.saveData();
                
            },
           
        },
            computed: {
                numeroProyectos() {
                    return this.proyectos.length;
                },
            },
            
           
    };

</script>