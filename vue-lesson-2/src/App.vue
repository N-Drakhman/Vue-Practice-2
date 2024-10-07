<script setup>
import { ref } from "vue";
import deleteButton from "./components/DeleteButton.vue";

function deleteTask(index) {
  tasks.value.splice(index, 1);
}

const isHidden = ref(false);

const tasks = ref(["dinner", "sleep", "work"]);
</script>

<template>
  <ul>
    <li v-for="(task, index) of tasks">
      <span @dblclick="isHidden = true" v-if="!isHidden">
        {{ index + 1 }} {{ task }}
      </span>

      <input
        v-model="tasks[index]"
        type="text"
        @keyup.enter="isHidden = !isHidden"
        v-if="isHidden"
      />

      <deleteButton @click="deleteTask(index)"></deleteButton>
    </li>
  </ul>
</template>

<style scoped>
li {
  display: block;
  position: relative;
  margin-bottom: 5px;

  width: 200px;
  padding: 12px;
  border-radius: 4px;

  background-color: rgb(90, 90, 90);
}

span {
  font-weight: bold;
}

input {
  width: 100px;
  padding: 5px;

  outline: none;
}
</style>
