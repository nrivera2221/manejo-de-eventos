<script>
import card from './card.vue';
export default {
    props: {
        pacientes: {
            type: Array,
            required: true
        }
    },
    components: {
        card,
    },
    methods: { 
        /*funcion para eliminar el paciente*/
    eliminarPaciente(index) {
        this.pacientes.splice(index, 1);
    },
  },
};
</script>

<template>
    <div v-if="pacientes.length > 0" class="d-flex flex-column  mt-4">
        <div class="text-center">
            <h3>Citas Medicas</h3>
        </div>
        <div class="d-flex flex-wrap">
            <div v-for="(paciente, i) in pacientes" :key="i" class="m-2">
                <card @eliminarPaciente="eliminarPaciente(i)" :gravedad="paciente.gravedad">
                    <template #default>
                        <div class="mb-2">
                            <h6 class="note-title">Paciente</h6>
                            <p class="note-text">{{ paciente.nombre }}</p>
                        </div>
                        <div class="mb-2">
                            <h6 class="note-title">Fecha</h6>
                            <p class="note-text">{{ paciente.fecha }}</p>
                        </div>
                        <div class="mb-2">
                            <h6 class="note-title">Hora</h6>
                            <p class="note-text">{{ paciente.hora }}</p>
                        </div>
                        <div class="mb-2">
                            <h6 class="note-title">Motivo</h6>
                            <p class="note-text">{{ paciente.motivo }}</p>
                        </div>
                    </template>
                </card>
            </div>
        </div>
        
    </div>
    <div v-else class="d-flex justify-content-center mt-3">
        <p class="text-danger">Aún no hay consultas registradas.</p>
    </div>
</template>