<script setup lang="ts">
import { ref } from 'vue'

interface Item {
  id: number
  name: string
  selected: boolean
}

const items = ref<Item[]>([
  { id: 1, name: 'Item 1', selected: false },
  { id: 2, name: 'Item 2', selected: true },
  { id: 3, name: 'Item 3', selected: false }
])

const updateItems = () => {
  items.value = [
    { id: 4, name: 'Item 4', selected: false },
    { id: 5, name: 'Item 5', selected: true }
  ]
}

const initScreen = () => {
  window.location.reload()
}
</script>

<template>
  <main>
    {{ items }}
    <a href="#" @click="updateItems">更新</a>
    <a href="#" @click="initScreen">初期化</a>
    <table class="table">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Selected</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>
            <input type="checkbox" id="item.id" v-model="item.selected" />
          </td>
        </tr>
      </tbody>
    </table>
  </main>
</template>

<style>
.table,
td,
th {
  border: 2px black solid;
}
</style>
