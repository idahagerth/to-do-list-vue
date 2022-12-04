<script setup>
import { ref } from "vue";

const message = ref("");
const messages = ref([]);

function addToDo() {
  messages.value.push({
    title: message.value,
    done: false,
  });
  message.value = "";
  console.log(messages.value);
}

function deleteToDo(index) {
  messages.value.splice(index, 1);
}
</script>

<template>
  <h1>My To Do List</h1>

  <div>
    <input v-model="message" />
    <button @click="addToDo">Add</button>
  </div>

  <ol>
    <li v-for="(check, index) in messages" :key="index">
      <input type="checkbox" @click="check.done = !check.done" />
      <span>{{ check.title }}</span>
      <button @click="deleteToDo(index)">remove</button>
    </li>
  </ol>
</template>

<style>
body {
  background-color: #fffaff;
  display: flex;
  justify-content: center;
}
input {
  border: none;
  font-size: x-large;
  background-color: #ccdad1;
  margin-bottom: 10px;
}
input[type="checkbox"] {
  width: 1.15em;
  height: 1.15em;
}
button {
  border-radius: 30px 30px 30px 30px;
  border: none;
  font-size: x-large;
  background-color: #8fb996;
}

h1 {
  display: flex;
  justify-content: center;
}
ol {
  list-style: none;
  margin: 0px;
  padding-inline-start: 0px;
}
li {
  padding: 1%;
  background-color: #ccdad1;
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
  font-size: x-large;
}
</style>
