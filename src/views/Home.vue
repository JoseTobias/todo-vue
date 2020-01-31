<template>
  <div class="home">
    <header class='page-header'>
        <h1>Tarefas <small>Cadastro</small></h1>
    </header>
    <todo-form />
    <todo-list />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import TodoForm from '@/components/TodoForm.vue'
import TodoList from '@/components/TodoList.vue'

export default {
  name: 'home',
  components: {
    TodoForm,
    TodoList
  }
}
</script>

<style>
.home {
  margin-top: 20px;
}

small {
  opacity: 0.7;
  font-size: 60%;
}

.btn {
  margin-right: 5px;
}

.markedAsDone {
  text-decoration: line-through;
  color: #777;
}

.tableActions {
  width: 116px;
}

.todoForm {
  padding-bottom: 60px;
}
</style>

