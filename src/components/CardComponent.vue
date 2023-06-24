<script setup>
  import { defineProps, defineEmits, ref } from 'vue';
  
  const props = defineProps({
    name: {
      type: String,
      default: 'No name',
    },
    mail: {
      type: String,
      default: 'no email',
    },
    index: {
      type: Number,
      required: true,
    },
  });
  
  const newName = ref('');
  const newMail = ref('');
  const showEditFields = ref(false);
  
  const borrarTarjeta = () => {
    emit('borrarTarjeta', props.index);
  };
  
  const modificarUsuario = () => {
    showEditFields.value = true;
  };

  const bajarModificacion = () => {
    showEditFields.value = false;
  };
  
  const guardarCambios = () => {
    if (newName.value && newMail.value) {
      emit('modificarUsuario', props.index, newName.value, newMail.value);
      showEditFields.value = false;
      newName.value = '';
      newMail.value = '';
    }
  };
  
  const emit = defineEmits(['borrarTarjeta', 'modificarUsuario']);
  </script>



<template>
    <div class="w-48 rounded shadow overflow-hidden mt-3 border border-white">
      <div class="inline-block">
        <img src="https://picsum.photos/40" alt="" @click="mensaje">
      </div>
      <div class="inline-block">
        <h2 class="text-sm font-semibold px-2">{{ props.name }}</h2>
        <p class="text-xs px-2">{{ props.mail }}</p>
      </div> <br>
  
      <div
        class="inline-block ml-4 bg-red-600 text-white rounded leading-0 py-0 px-1 ms-10 hover:cursor-pointer hover:bg-red-800"
        @click="borrarTarjeta"
      > X </div>
  
      <button class="bg-blue-600 text-white rounded py-0.5 px-2 mt-2 ms-12" @click="modificarUsuario">
        Modificar
      </button>
  
    </div>
  
    <div class="flex flex-col items-end" style="flex-direction: row-reverse;">
    <div v-show="showEditFields" >
      <input v-model="newName" type="text" placeholder="Nuevo nombre" class="border rounded" style="color: black;"><br><br>
      <input v-model="newMail" type="text" placeholder="Nuevo email" class="border rounded" style="color: black;"><br>
      <button class="bg-green-600 px-2 py-1 rounded mt-2" @click="guardarCambios">Guardar</button>
      <span  class="inline-block ml-4 bg-red-600 text-white rounded leading-0 py-0 px-1 ms-10 hover:cursor-pointer hover:bg-red-800"
        @click="bajarModificacion">
        X
      </span>
    </div>
</div>

  </template>
  

  