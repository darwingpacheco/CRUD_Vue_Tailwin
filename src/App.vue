<script setup>
import { ref } from 'vue';
import CardComponent from './components/CardComponent.vue';
import postComponent from './components/postComponent.vue';
const users = ref([
  {
    name: 'Camila',
    foto: 'https://picsum.photos/100'
  },
  {
    name: 'Maria Fernanda',
    foto: 'https://picsum.photos/500'
  },

  {
    name: 'Señor Equis',
   foto: 'https://picsum.photos/354'

  },
  {
  name: 'Juan Carlos',
   foto: 'https://picsum.photos/223'

  },
]);
const post = ref([
  {
    persona: 'Mariano Perez',
    imgPost: 'https://picsum.photos/100',
    tiempo: 'Hace 10 minutos'
  },
]);

</script>

<template>
  <div>
    <div class="flex justify-between">
      <h1 class="text-2xl mr-4">Historias</h1>
      <button class="bg-blue-300 text-black" id="todos">Todos</button>
    </div>
    <div class="grid grid-flow-col justify-stretch">
      <div v-for="(user, index) in users" :key="index">
        <CardComponent
          :name="user.name"
          :index="index"
          :foto="user.foto"
        />
    
      </div>
    </div><br>
    <div>
      <div v-for="(p, index) in post" :key="index">
        <postComponent
          :persona="p.persona"
          :imgPost="p.imgPost"
          :tiempo="p.tiempo"
          :index="index"
        />
    
      </div>
    </div>
  </div>
</template>

<style scoped>
#todos {
  border-bottom: 12px;
}

.info-container {
  margin-top: 10px;
  text-align: center;
}
</style>


