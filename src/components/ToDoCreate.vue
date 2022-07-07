<script setup>
// import { reactive } from 'vue'



// function todosave(e) {
//   const value = e.target.value.trim()
//   if (value) {
//     todos.value.push({
//       id: Date.now(),
//       title: value,
//       completed: false
//     })
//     e.target.value = ''
//   }
// }

const props = defineProps({
  show: Boolean
})

// const toDoTitle = ref("")
</script>

<template>
  <Transition name="modal">
    <div v-if="show" class="todo-mask">
      <div class="todo-wrapper">
        <div class="todo-container">
          <div class="todo-body">
            <input type="checkbox" class="toggle" v-model="todo.status" />
            <input v-model="toDoTitle" class="text" autofocus placeholder="task name">
            {{ toDoTitle }}
            <textarea class="multiline" placeholder="notes"></textarea>
            <button class="todo-default-button" @click="$emit('close')">
              cancel
            </button>
            <button class="todo-default-button" @click="todosave">
              save <!-- on save, generate card -->
            </button>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style>
@import '../assets/base.css';

.todo-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

/* wrapper sets location */
.todo-wrapper {
  display: table-cell;
  vertical-align: middle;
}

/* container sets look */
.todo-container {
  width: 300px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 12px;
  
  border: 2px solid #000;
  transition: all 0.3s ease;
}

.todo-container:hover {
  box-shadow: 6px 6px 0px #000000;
}

.todo-body {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 8px 12px;
  gap: 12px;
}

.todo-default-button {
  float: right;
}

/*
  * The following styles are auto-applied to elements with
  * transition="modal" when their visibility is toggled
  * by Vue.js.
  *
  * You can easily play with the modal transition by editing
  * these styles.
  */

.todo-enter-from {
  opacity: 0;
}

.todo-leave-to {
  opacity: 0;
}

.todo-enter-from .todo-container,
.todo-leave-to .todo-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}


</style>