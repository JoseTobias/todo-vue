<template>
  <table class='table'>
    <thead>
      <tr>
        <th>Descrição</th>
        <th class='tableActions'>Ações</th>
      </tr>
    </thead>
    <tbody v-for="todo in todos" :key="todo.id">
      <tr>
        <td :class="todo.done ? 'markedAsDone' : ''">{{ todo.description }}</td>
        <td>
          <button class='btn btn-success' v-if="!todo.done" @click="marked(todo, true)">
            <i class='fas fa-check'></i>
          </button>
          <button class='btn btn-warning' v-if="todo.done" @click="marked(todo, false)">
            <i class='fas fa-undo'></i>
          </button>
          <button class='btn btn-danger' v-if="todo.done" @click="remove(todo)">
            <i class='fas fa-trash'></i>
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import bus from '@/scripts/bus.js'

export default {
  data () {
    return {
      URL: "http://localhost:3003/api/todos",
      todos: []
    }
  },
  methods: {
    refresh (description ='') {
      const search = description ? `&description__regex=/${description}/` : ''
      fetch(this.URL + '?sort=-createdAt' + search)
      .then(resp => resp.json())
      .then(resp => {this.todos = resp})
    },
    marked (todo, choice) {
      fetch(this.URL+ '/' + todo._id, {
        method: "PUT",
        headers: {"Content-Type": "application/x-www-form-urlencoded"},
        body: new URLSearchParams({...todo, done: choice})})
      .then(() => this.refresh())
    },
    remove (todo) {
      fetch(this.URL + '/' + todo._id, {method: "DELETE"})
      .then(() => this.refresh())
    }
  },
  mounted () {
    this.refresh()
  },
  created () {
    bus.$on('refresh', (data) => this.refresh(data))
  }
}
</script>

