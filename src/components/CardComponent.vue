<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  name: {
    type: String,
    default: 'No name',
  },
  foto: {
    type: String,
    default: 'No image',
  },
  index: {
    type: Number,
    required: true,
  },
});

</script>

<template>
    <div>
      <div>
        <img :src="props.foto" alt="" class="cursor-pointer w-32 h-32 object-cover pr-3">
      </div>
      <div>
        <h2 class="text-sm font-semibold px-2">{{ props.name }}</h2>
      </div>
    </div>
</template>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  align-items: center;
}

img {
  width: 200px; /* Ajusta el ancho para hacer la imagen más grande */
  height: 200px; /* Ajusta la altura para mantener la relación de aspecto */
  border-radius: 10%;
}

h2 {
  margin-top: 10px;
  font-size: 14px;
}
</style>
