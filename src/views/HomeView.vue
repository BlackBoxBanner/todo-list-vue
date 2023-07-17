<script setup lang="ts">
import {ref, watch} from "vue"
import Button from "@/components/Button.vue";

interface Todos {
  id: number,
  todo: string
}

const todoAddRef = ref("")
const todos = ref<Todos[]>([])
const result = ref<Todos[]>([])

function addTotoHandler(todo: string) {
  if (!todo) return
  todos.value.push({todo, id: Math.random()})
  todoAddRef.value = ""
}

function removeTotoHandler(id: number) {
  result.value = []
  todos.value = todos.value.filter(function (itemsId) {
    return itemsId.id !== id
  })
  console.log(todos.value)
}
</script>

<template>
  <main class="h-screen overflow-x-auto min-h-screen bg-neutral-900 break-words md:px-80 md:pt-14 text-neutral-300">
    <div class="flex flex-col items-center h-full gap-4">
      <h1 class="text-4xl">Todo list</h1>
      <div class="border border-neutral-300 rounded p-4 w-full flex flex-col gap-4">
        <div class="flex justify-between gap-4">
          <div class="rounded w-full p-1 px-2 border border-neutral-50">
            <input type="text" v-model="todoAddRef" class="w-full">
          </div>
          <Button class="w-32" @click="addTotoHandler(todoAddRef)">Add todo</Button>
        </div>
        <div v-for="todo in todos as Todos[]"
             class="rounded w-full p-1 px-2 border border-neutral-50 flex gap-4 items-center">
          <button
              @click="removeTotoHandler(todo.id)"
              class="w-8 h-8 rounded bg-neutral-700 hover:bg-neutral-600 transition-colors ease-in-out duration-100">x
          </button>
          <div>{{ todo.todo }}</div>
        </div>
      </div>
    </div>
  </main>
</template>

