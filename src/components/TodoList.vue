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
          <button class='btn btn-success' v-if="!todo.done">
            <i class='fas fa-check'></i>
          </button>
          <button class='btn btn-warning' v-if="todo.done">
            <i class='fas fa-undo'></i>
          </button>
          <button class='btn btn-danger' v-if="todo.done">
            <i class='fas fa-trash'></i>
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  data () {
    return {
      todos: [
        {
          "done": true,
          "_id": "5dc0bf54029f4d3ecae9a86e",
          "description": "pagar cartão"
        },
        {
          "done": false,
          "_id": "5dc0bf6e029f4d3ecae9a86f",
          "description": "concluir curso de react"
        },
        {
          "done": false,
          "_id": "5dc7fee6985fbe34f041022f",
          "description": "teste"
        },
        {
          "done": false,
          "_id": "5dc7ffed985fbe34f0410230",
          "description": "estudar pt"
        }
      ]
    }
  }
}
</script>

