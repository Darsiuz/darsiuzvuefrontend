<script setup lang="ts">
import { ref } from 'vue'

const newTask = ref<string>('')
const tasks = ref<string[]>([])

const Agregar = () => {
  if (newTask.value.trim().length === 0) return
  tasks.value.push(newTask.value)
  newTask.value = ''
}
const Eliminar = (index: number) => {
  tasks.value.splice(index, 1)
}
</script>

<template>
  <div>
    <h1>Lista de tareas</h1>
    <div class="input-group mb-3">
      <input v-model="newTask" placeholder="Nueva tarea" class="form-control" />
      <button class="btn btn-primary" @click="Agregar">Agregar</button>
    </div>

    <ul class="list-group list-group-flush">
      <li v-for="(task, index) in tasks" :key="index" class="list-group-item center">
        <div class="d-flex justify-content-between align-items-center">
          <span>{{ task }}</span>
          <button class="btn btn-danger btn-sm float-end" @click="Eliminar(index)">X</button>
        </div>
      </li>
    </ul>

  </div>
</template>

<style scoped>
input {
  margin-right: 8px;
}
</style>
