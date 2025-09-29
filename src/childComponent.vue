<script setup>
import {ref} from 'vue'

const props = defineProps({
  todo: Object
})

const emit = defineEmits(['sendIdForDelete','sendIdForSwitch'])

function sendIdForDelete() {
  emit('sendIdForDelete', props.todo.id)
}
function sendIdForSwitch() {
  emit('sendIdForSwitch', props.todo.id)
}
</script>

<template>
  <ul>
    <li> {{ todo.text }} : {{ todo.completed }}
      <button @click="sendIdForDelete">✖️</button>
      <button @click="sendIdForSwitch">↻</button>
    </li>
  </ul>
</template>

<style scoped>

</style>