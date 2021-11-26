<template>
  <div>
    <img width="50" height="50" alt="Vue logo" src="./assets/logo.png" />
    <div>{{ title }}</div>
    <FormTodo @cadastrar="addToList($event)"/>
    <TodoList
      @deleteById="removeFromList($event)"
      @editById="editFromList($event)"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import FormTodo from './components/FormTodo.vue'
import TodoList from './components/TodoList.vue'

export default {
  components: {
    FormTodo,
    TodoList
  },
  data() {
    return {
      title: 'Vue TodoList',
      tasks: []
    }
  },
  methods: {
    addToList (text) {
      this.tasks.push(text)
    },
    removeFromList (index) {
      this.tasks.splice(index, 1)
    },
    editFromList (event) {
      this.tasks.splice(event.index, 1, event.text)
    }
  }
}
</script>
<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
