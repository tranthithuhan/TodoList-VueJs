<template>
  <div class="ui centered card" >
    <div class="content" v-show="!isEditing">
      <div class='extra content'>
        <a class='right floated' v-on:click="showForm">
          <i class='edit icon'></i>
        </a>
        <a class='right floated' v-on:click="deleteTodo(todo)">
          <i class='trash icon'></i>
        </a>
      </div>
      <div class="header">{{todo.title}}</div>
    </div>

    <div class="content" v-show="isEditing">

      <div class="ui form">
        <div class='extra content'>
          <a class='right floated' v-on:click="hideForm">
            <i class='close icon'></i>
          </a>
        </div>
        <div class="field">
          <label>Title</label>
          <input type="text" placeholder="Title" v-model="todo.title"/>
        </div>
      </div>
    </div>

    <div class='ui bottom attached green basic button' v-show="!isEditing &&todo.done" disabled>
      <i class='check icon green'></i> Completed
    </div>
    <div class='ui bottom attached red basic button' v-show="!isEditing && !todo.done">
      Pending ...
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  name: 'todo',
  props: ['todo'],
  data () {
    return {isEditing: false}
  },
  methods: {
    showForm () {
      this.isEditing = true
    },
    hideForm () {
      this.isEditing = false
    },
    deleteTodo (todo) {
      this.$emit('delete-todo', todo)
    }
  }
}
</script>

<style scoped>

</style>
