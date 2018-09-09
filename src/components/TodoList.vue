<template>
  <div>
    <div class="ui header medium centered">
      Completed tasks:
        {{
        todos.filter(todo => {return todo.done}).length
        }}
    </div>
    <div class="ui header medium centered">
      Pending tasks:
        {{
        todos.filter(todo => {return !todo.done}).length
        }}
    </div>
    <todo v-for="todo in todos"
          v-bind:todo="todo"
          v-bind:key="todo.id"
          v-on:delete-todo="deleteTodo"/>
  </div>
</template>

<script type="text/javascript">
import Todo from './Todo'
export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      const index = this.todos.indexOf(todo)

      this.todos.splice(index, 1)
    }
  }
}
</script>
