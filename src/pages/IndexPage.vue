<template>
  <div id="form">
    <q-form @submit="addNewTodo">
      <q-input outlined color="grey-8" bg-color="white" v-model="inputText" label="Digite uma tarefa." class="input q-mx-auto red-1">
        <template #prepend>
          <q-icon name="event" />
        </template>
      </q-input>
    </q-form>

    <div class="list-todos q-gutter-y-md q-mx-auto" v-if="todos.length">
      <q-field hide-bottom-space borderless outlined bg-color="grey-10" clearable v-for="todo in todos" :for="todo.id" :key="todo.id">
        <template #control>
          <div class="self-center no-outline text-white">
            {{ todo.name }}
          </div>
        </template>

        <template #append>
          <q-icon color="grey-7" name="delete" class="cursor-pointer" @click="removeTodo(todo)" />
        </template>
      </q-field>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { v4 as uuidV4 } from 'uuid';

interface Todo {
  name: string;
  id: string;
  done: boolean
}

const inputText = ref('');
const todos = ref<Todo[]>([]);

function addNewTodo() {
  const todo = {
    id: uuidV4(),
    name: inputText.value,
    done: false,
  };

  todos.value.push(todo);
  inputText.value = '';
}

function removeTodo(todo: Todo) {
  const filteredTodos = todos.value.filter((oldTodo) => oldTodo.id !== todo.id);

  todos.value = filteredTodos;
}
</script>

<style lang="scss" scoped>
.input {
  max-width: 500px;
  margin-top: 64px;
}

.list-todos {
  margin-top: 56px;
  max-width: 755px;
  width: 100%;
  padding: 4px 16px;
  border-radius: 4px;

  div {
    padding: 16px;
    font-size: 24px;
  }
}
</style>
