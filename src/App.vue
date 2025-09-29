<script setup>
import {ref} from 'vue'
import childComponent from './childComponent.vue'

const todos = ref([
  {id: 1, text: 'помыть посуду', completed: false},
  {id: 2, text: 'убраться в комнате', completed: false},
  {id: 3, text: 'выкинуть мусор', completed: false},
  {id: 4, text: 'сходить в магазин', completed: false}
])

let falseTask = ref(0)

todos.value.forEach((e) => {
  if (e.completed === false) {
    falseTask.value += 1
  }
})


const deleteTodoId = (idToDelete) => {
  todos.value = todos.value.filter((todo) => idToDelete !== todo.id)
  falseTask.value--
}
const switchCompleted = (idToSwitch) => {
  const myElement = todos.value.find(element => idToSwitch === element.id)
  myElement.completed = !myElement.completed
  if (myElement.completed) {
    falseTask.value--
  } else {
    falseTask.value++
  }
}


</script>

<template>
  <h3>Список дел на 29.09.2025</h3>
  <p>Кол-во невыполненных задач: {{ falseTask }}</p>
  <childComponent
      v-for="todo in todos" :todo="todo"
      @sendIdForDelete="deleteTodoId"
      @sendIdForSwitch="switchCompleted"
  />
</template>

<style scoped>


</style>
