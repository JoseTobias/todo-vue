<template>
    <div role='form' class='todoForm row'>
        <div class='col-xs-12 col-sm-9 col-md-10'>
            <input id='description' class='form-control'
            placeholder='Cadastre uma tarefa'
            v-model="description" />
        </div>
        <div class='col-xs-12 col-sm-3 col-md-2'>
            <button class='btn btn-primary'>
                <i class='fas fa-plus'></i>
            </button>
            <button class='btn btn-info'>
                <i class='fas fa-search'></i>
            </button>
            <button class='btn btn-default' @click="clear()">
                <i class='fas fa-times'></i>
            </button>
        </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      description: '',
      URL: 'http://localhost:3003/api/todos'
    }
  },
  methods: {
    add() {

    },
    search() {
    
    },
    clear() {
      this.description = ''
    }
  }
}
</script>
