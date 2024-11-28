<script>
export default {
    props: {
        gravedad: {
        type: String,
        required: true,
        },
    },
    methods: {
        //funcion para agregar la clase del color correspondiente segun la gravedad
        getCintaClass(gravedad) {
            if (gravedad === 'Baja') {
                return 'green';
            } else if (gravedad === 'Media') {
                return 'yellow';
            } else if (gravedad === 'Alta') {
                return 'red';
            }
            return '';
        },
        //agregar el color al button segun la gravedad 
        getButtonClass(gravedad) {
            if (gravedad === 'Baja') {
                return 'btn-success';  // Bootstrap clase para botón verde
            } else if (gravedad === 'Media') {
                return 'btn-warning';  // Bootstrap clase para botón amarillo
            } else if (gravedad === 'Alta') {
                return 'btn-danger';  // Bootstrap clase para botón rojo
            }
            return 'btn-primary';  // Clase por defecto
        },
    },
};
</script>
<template>
    <div class="p-3 my-3" :class="['sticky-note', getCintaClass(gravedad)]">
        <div class="d-flex flex-column">
            <slot/>
        </div>
        <div class="d-flex justify-content-end">
            <button
                :class="['btn', getButtonClass(gravedad)]"
                @click="$emit('eliminarPaciente')"
            >
            Eliminar
            </button>
        </div>
    </div>
</template>
<style scoped>
.sticky-note {
    width: 210px;
    box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.2);
    border-radius: 8px;
    position: relative;
  }
  
  .sticky-note.red{
    background-color: #ffcccc; 
    border: 1px solid #ff0000; 
  }
  .sticky-note.green{
    background-color: #ccffcc; 
    border: 1px solid #008000; 
  }
  .sticky-note.yellow{
    background-color: #fffeca; 
    border: 1px solid #e0d500; 
  }
  .sticky-note::before {
    content: "";
    position: absolute;
    top: 0;
    left: 20px;
    width: 40px;
    height: 10px;
    background-color: #f1c40f;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
  }
  .sticky-note.red::before {
    content: "";
    position: absolute;
    top: 0;
    left: 20px;
    width: 40px;
    height: 10px;
    background-color: #ff0000; /* Rojo */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
}

.sticky-note.green::before {
    content: "";
    position: absolute;
    top: 0;
    left: 20px;
    width: 40px;
    height: 10px;
    background-color: #008000; /* Verde */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
}
  .note-title {
    font-weight: bold;
    margin-bottom: 0;
  }
  
  .note-text {
    margin-top: 0;
    font-size: 0.9rem;
    color: #333;
  }  
</style>