<script setup>
import {ref, computed} from 'vue'

const counter = ref(0);
const arraynumeros = ref([]);

const increment = () => {
    counter.value ++;
};
const disminuir = () => {
    counter.value --;
};
const reset = () => {
    counter.value = 0;
};
const addtoarray = () => {
    arraynumeros.value.push(counter.value);
};
const classCounter = computed(() => {
  if(counter.value === 0) {
    return 'zero'
  }
  if(counter.value > 0) {
    return 'positive'
  }
  if(counter.value < 0) {
    return 'negative'
  }
});
const blockNumber = computed(() => {
    const number = arraynumeros.value.find((num) => num === counter.value);
    return number || number === 0;
});
</script>

<template>
    <div class="container">
      <h2 :class="classCounter">Contador: {{ counter }}</h2><br>
      <div class="btn-group">
        <button @click="increment" class="btn btn-success">Incrementar</button>
        <button @click="disminuir" class="btn btn-danger">Disminuir</button>
        <button @click="reset" class="btn btn-secondary">Reset</button>
        <button @click="addtoarray" :disabled="blockNumber" class="btn btn-primary">Agregar</button>
      </div>
      <ul class="list-group mt-4">
        <li v-for="numerito, index in arraynumeros" :key="index" class="list-group-item">
          {{ numerito }}
        </li>
      </ul>
    </div>
    
</template>

<style>
body {
  background-color: black;
}
.negative {
    color: red;
}

.positive {
    color: green;
}
.zero {
  color: peru;
}
</style>