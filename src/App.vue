<script setup>
import { ref } from 'vue'
// import Modal from './components/ToDoCreate.vue'
import ToDoCard from './components/ToDoCard.vue'

// const newToDo = ref(false)

const newTodoText = ref('')
// hard-coded data
const toDoItems = ref([
    { id: 1, toDoName: 'finish project', toDoStatus: false, toDoNotes: 'lorem ipsum' },
    { id: 2, toDoName: 'read chapter 5', toDoStatus: false, toDoNotes: '' },
    { id: 3, toDoName: 'turn in hw', toDoStatus: false, toDoNotes: 'lorem ipsum' }
])

let nextTodoId = 4

function addNewTodo() {
  toDoItems.value.push({
    id: nextTodoId++,
    toDoName: newTodoText.value
  })
  newTodoText.value = ''
}
</script>

<template>
  <header>
    <!-- logo -->
    <p>node planner</p>
    <!-- search bar -->
    <!-- hamburger menu -->
  </header>

  <form v-on:submit.prevent="addNewTodo">
    <label for="new-todo">Add a todo</label>
    <input
      v-model="newTodoText"
      id="new-todo"
      placeholder="to do name"
    />
    <button>Add</button>
  </form>

  <ul>

    <to-do-card
      v-for="(toDoItem, index) in toDoItems"
      :key="toDoItem.id"
      :toDoName="toDoItem.toDoName"
      :toDoStatus="toDoItem.toDoStatus"
      :toDoNotes="toDoItem.toDoNotes"
      @remove="toDoItems.splice(index, 1)"
    ></to-do-card>

  </ul>

  <!-- add todo button 
  <button id="add-button" @click="newToDo = true"></button>

  <Teleport to="body">
    <modal :show="newToDo" @close="newToDo = false">
    </modal>
  </Teleport>-->

  <footer></footer>
</template>   

<style>
@import './assets/base.css';

#app {
  /* max-width: 1280px; */
  margin: 0 auto;
  /* padding: 2rem; */

  font-weight: normal;
}

/* dotted background */
body {
  background-image: radial-gradient(#C4C4C4 10%, transparent 10%);
  background-size: 15px 15px;
}

header {
  /* imported from figma */
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 20px 32px;
  gap: 240px;

  background-color: #FFF;
  border-bottom: 2px solid #000000;

}

footer {
  position: fixed;
  bottom: 0;
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 32px;

  background-color: #FFF;
  border-top: 2px solid #000000;
}

#add-button {
  position: fixed;
  right: 32px;
  bottom: 68px;

  cursor: pointer;

  height: 56px;
  width: 56px;
  background-image: url(./components/icons/add-card-default.svg);
  background-color: transparent;
  outline: none;
  border: 0;
}

#add-button:hover {
  background-image: url(./components/icons/add-card-hover.svg);
}

#add-button:active {
  background-image: url(./components/icons/add-card-active.svg);
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a {
  text-decoration: none;
  transition: 0.4s;
}

/* @media (hover: hover) { 
    a:hover {
      background-color: hsla(160, 100%, 37%, 0.2);
    }
  } */

@media (min-width: 1024px) {
  /* body {
      display: flex;
      place-items: center;
    } */

  /* #app {
      display: grid;
      grid-template-columns: 1fr 1fr;
    } */

  header {
    display: flex;
    place-items: center;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>