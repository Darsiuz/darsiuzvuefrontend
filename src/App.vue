<script setup lang="ts">
import { ref } from 'vue'

const newTask = ref<string>('')
const tasks = ref<string[]>([])

const Agregar = () => {
  if (newTask.value.trim().length === 0) return
  tasks.value.push(newTask.value)
  newTask.value = ''
}
</script>

<template>
  <div>
    <h1>Lista de tareas</h1>
    <input v-model="newTask" placeholder="Nueva tarea" />

    <button @click="Agregar">Agregar</button>

    <ul>
      <li v-for="(task, i) in tasks" :key="i">
        {{ task }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
input {
  margin-right: 8px;
}
</style>
