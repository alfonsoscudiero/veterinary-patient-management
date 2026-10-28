<script setup>
  import {ref, reactive, watch, onMounted} from 'vue';
  import { uid } from 'uid';
  import Header from './components/Header.vue';
  import Formulario from './components/Formulario.vue';
  import Paciente from './components/Paciente.vue';

  const pacientes = ref([]);

  // Para agrupar datos (atributos) que tienen que ir juntos se recomienda usar State Reactive (siempre es un Objeto)
  const paciente = reactive({
    id: null, // formulario todavía no tiene un paciente identificado
    nombre: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: '',
  });

  const guardarLocalStorage = () => {
    localStorage.setItem('pacientes', JSON.stringify(pacientes.value));
  }

  watch(pacientes, () => {
    guardarLocalStorage();
  }, { deep: true });

  onMounted(() => {
    const pacientesStorage = localStorage.getItem('pacientes');
    if (pacientesStorage) {
      pacientes.value = JSON.parse(pacientesStorage);
    }
  })
    
  const guardarPaciente = () => {
    if(paciente.id) {
      // Actualizar un paciente existente
      const { id } = paciente;
      
      const i = pacientes.value.findIndex((pacienteState) => {
        return pacienteState.id === id;
      })

      if (i !== -1) {
        // Actualiza solamente cuando encuentra al paciente en el arrelo pacientes
        pacientes.value[i] = {...paciente};
      }

      // Reiniciar todos los campos del formulario
      Object.assign(paciente, {
        id: null,
        nombre: '',
        propietario: '',
        email: '',
        alta: '',
        sintomas: ''
      });
    } else {
      // Registrar un paciente nuevo
      pacientes.value.push({
        // creamos una copia del Objeto paciente con spread operator
        ...paciente,
        id: uid() // reemplaza el valor id: null que venía del objeto original y genera su identificador en la copia que guardas
      });
  
      // Reiniciar el Objeto paciente
        paciente.id = null; // reestablecer el identificador del formulario a su valor inicial
        paciente.nombre = '';
        paciente.propietario = '';
        paciente.email = '';
        paciente.alta = '';
        paciente.sintomas = '';
      }
    }
    
  const actualizarPaciente = (id) => {
    const pacienteEditar = pacientes.value.filter((paciente) => {
      return paciente.id === id;
    })[0]
    Object.assign(paciente, pacienteEditar);
  }

  const eliminarPaciente = (id) => {
    pacientes.value = pacientes.value.filter((paciente) => {
      return paciente.id !== id;
    })
  }
  
  
</script>

<template>
  <div class=" container mx-auto mt-20">
    <Header />

    <div class=" mt-12 md:flex">
      <Formulario 
        v-model:nombre="paciente.nombre"
        v-model:propietario="paciente.propietario"
        v-model:email="paciente.email"
        v-model:alta="paciente.alta"
        v-model:sintomas="paciente.sintomas"
        @guardar-paciente="guardarPaciente"
        @actualizar-paciente="actualizaPaciente"
        :id="paciente.id"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scrow">
        <h3 class="font-black text-3xl text-center">
          Administra tus Pacientes
        </h3>
        <div v-if="pacientes.length > 0">
          <p class="text-lg mt-5 text-center mb-10">
            Información de
            <span class="text-indigo-600 font-bold">Pacientes</span>
          </p>
          <Paciente 
            v-for="paciente in pacientes"
            :paciente="paciente"
            @actualizar-paciente="actualizarPaciente"
            @eliminar-paciente="eliminarPaciente"
          />
        </div>
        <p v-else class="mt-20 text-2xl text-center">
          No hay Pacientes
        </p>
      </div>
    </div>    
  </div>
</template>
