<script setup>
import { defineProps, ref } from 'vue';

const props = defineProps({
  persona: {
    type: String,
    default: 'No name',
  },
  tiempo: {
    type: String,
    default: 'No image',
  },
  imgPost: {
    type: String,
    default: 'No image',
  },
  index: {
    type: Number,
    required: true,
  },
});

const counter = ref(0);
const counterNoLike = ref(0);
const isLiked = ref(false);
const isLikedNoLike = ref(false);  // Variable booleana para controlar si el contador ha sido incrementado

const incrementCounter = () => {
  if (!isLiked.value) {
    counter.value++;
    isLiked.value = true;
  }
};

const incrementCounterNoLike = () => {
  if(!isLikedNoLike.value){
    counterNoLike.value++;
    isLikedNoLike.value=true;
  }
};
</script>

<template>
  <div class="image-container">
    <div class="flex flex-row justify-start">
      <img src="img/man.png" alt="" class="user-icon">
      <h2 class="text-sm font-semibold px-">{{ props.persona }}</h2>
    </div>
    <h2 class="text-sm font-semibold px-">{{ props.tiempo }}</h2>

    <img :src="props.imgPost" alt="" class="full-width-image">
    <div class="heart-container">
      <img src="img/corazon.png" alt="" @click="incrementCounter" class="heart-icon">
      <span>{{ counter }}</span>

      <div class="heart-container ps-10">
        <img src="img/dont-like-symbol.png" alt="" @click="incrementCounterNoLike" class="heart-icon">
        <span>{{ counterNoLike }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.image-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.full-width-image {
  width: 100%;
  border-radius: 10px;
  object-fit: cover;
  object-position: center;
}

.heart-container {
  display: flex;
  align-items: center;
}

.heart-icon {
  width: 26px; /* Ajusta el tamaño del ícono de corazón */
  height: 26px;
  cursor: pointer;
  margin-right: 8px; /* Ajusta el espacio entre la imagen y el contador */
}
.user-icon {
  width: 40px; /* Ajusta el tamaño del ícono de corazón */
  height: 40px;
  cursor: pointer;
  border-radius: 10%;
}

h2 {
  margin-top: 10px;
  font-size: 14px;
}
</style>
