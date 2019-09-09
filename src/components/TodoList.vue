<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo-item v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo"></todo-item>
  </div>
</template>

<script type = "text/javascript" >

import TodoItem from './TodoItem.vue';

export default {
  props: ['todos'],
  components: {
    TodoItem,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
  },
};
</script>