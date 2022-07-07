<script setup>

defineProps(['toDoName', 'toDoStatus', 'toDoNotes'])
defineEmits(['removeItem'])
</script>

<template>
  <li>
    <div class="todo-container">
      <div class="todo-body">
        <button @click="$emit('remove')">delete</button>
        <label id="todo-title">
          <input v-model="toDoStatus" type="checkbox">
          {{ toDoName }}
        </label>
        <p id="todo-notes">{{ toDoNotes }}</p>
      </div>
    </div>
  </li>
</template>  

<style>
.todo-container {
  width: 268px;
  padding: 12px;
  background-color: #fff;
  border-radius: 12px;

  border: 2px solid #000;
  transition: all 0.3s ease;
}

.todo-container:hover {
  box-shadow: 6px 6px 0px #000000;
  transform: translate(0px, -6px)
}

.todo-body {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 8px;
  gap: 8px;
}

.todo-default-button {
  float: right;
}

#todo-title {
  font-size: 24px;
}

#todo-notes {
  font-style: italic;
}
</style>