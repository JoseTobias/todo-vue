<template>
  <nav class='navbar navbar-dark bg-dark'>
    <div class='container flex-nowrap justify-content-center'>
      <div class='navbar-header'>
        <router-link to="/" class='navbar-brand'>
          <i class='far fa-calendar-check'></i> TodoApp
        </router-link>
      </div>

      <div id='navbar' class='navbar-collapse d-none d-md-flex'>
        <ul class='nav navbar-nav flex-row'>
          <li class='pl-3 pr-3'><router-link to="/" class='text-light text-decoration-none'>Tarefas</router-link></li>
          <li class='pl-3 pr-3'><router-link to="/about" class='text-light text-decoration-none'>Sobre</router-link></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
}
</script>

<style scoped>

</style>
