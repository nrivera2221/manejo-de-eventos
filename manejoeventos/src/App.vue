<script>
import Formulario from './components/Formulario.vue';
import Tablero from './components/Tablero.vue';

export default {
  components: {
    Formulario,
    Tablero
  },
  data() {
    return {
      pacientes: []
    };
  },
  methods: {
    /**funcion para agregar pacientes al array*/
    agregarPaciente(paciente) {
      this.pacientes.push(paciente);
    }
  }
};
</script>

<template>
  <div class="container mt-4 ">
    <div class="border border-secondary p-3 rounded">
      <formulario @nuevoPaciente="agregarPaciente" /> <!--emite el paciente-->
    </div>
    <div>
      <tablero :pacientes="pacientes" /> <!--envia el arreglo paciente a el tablero-->
    </div>
  </div>
</template>
<style scoped>
</style>