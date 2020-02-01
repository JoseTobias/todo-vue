<template>
    <div role='form' class='todoForm row'>
        <div class='col-xs-12 col-sm-9 col-md-10'>
            <input id='description' class='form-control'
            placeholder='Cadastre uma tarefa'
            v-model="description" />
        </div>
        <div class='col-xs-12 col-sm-3 col-md-2'>
            <button class='btn btn-primary' @click="add()">
                <i class='fas fa-plus'></i>
            </button>
            <button class='btn btn-info' @click="search()">
                <i class='fas fa-search'></i>
            </button>
            <button class='btn btn-default' @click="clear()">
                <i class='fas fa-times'></i>
            </button>
        </div>
    </div>
</template>

<script>
import bus from '@/scripts/bus.js'
export default {
  data () {
    return {
      description: '',
      URL: 'http://localhost:3003/api/todos'
    }
  },
  methods: {
    add() {
      fetch(this.URL, {
        method: "POST",
        headers: {"Content-Type": "application/x-www-form-urlencoded"},
        body: new URLSearchParams({description: this.description, done: false})})
      .then(() => this.clear())
    },
    search() {
      bus.$emit('refresh', this.description)
    },
    clear() {
      this.description = ''
      bus.$emit('refresh')
    }
  },
  created () {
    bus.$on('getDescription', () => bus.$emit('refresh', this.description))
  }
}
</script>
