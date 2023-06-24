<script setup>
import { ref } from 'vue';
import CardComponent from './components/CardComponent.vue';


    const users = ref([
      {
        name: 'Darwin Gomez',
        mail: 'darwin@gmail.com',
      },
      {
        name: 'Andrey Pacheco',
        mail: 'pacheco@gmail.com',
      },
    ]);

    const borrarTarjeta = (index) => {
      alert('¿Estás seguro de eliminar el usuario?', index);
      users.value.splice(index, 1);
    };

    const modificarUsuario = (index, newName, newMail) => {
      const user = users.value[index];
      user.name = newName;
      user.mail = newMail;
    };

    const name = ref('');
    const mail = ref('');

    const addUser = () => {
      const newUser = {
        name: name.value,
        mail: mail.value,
      };

 

      users.value.unshift(newUser);
      name.value = '';
      mail.value = '';
    };

</script>

<template>
  <div>
    <h1 class="text-2x1">
      HOLA MUNDO
    </h1>
    <input type="text"  v-model="name" placeholder="Escriba su nombre" class="border rounded" style="color: black; "><br><br>
    <input type="text" v-model="mail" placeholder="email" class="border rounded" style="color: black;"><br>
    <button class="bg-green-600 px-2 py-1 rounded mt-2" @click="addUser">Añadir</button>
    <div class="space-y-2">
      <CardComponent
        v-for="(user, index) in users" :key="index"
        :name="user.name"
        :mail="user.mail"
        :index="index"
        @borrarTarjeta="borrarTarjeta"
        @modificarUsuario="modificarUsuario"
      />
    </div>

  </div>

</template>

<style scoped>

</style>
