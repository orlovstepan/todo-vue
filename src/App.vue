<template>
  <div id="app">
    <h1>Todo List</h1>
    <ul>
      <li v-bind:class="(todo.completed ? 'completed' : 'not-completed')" v-for="(todo, index) in todos" :key="index">
        <TodoItem :title="todo.title" :completed="todo.completed" @update:completed="updateTodo(index, $event)" />
      </li>
    </ul>
    <input class="add-todo" v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new todo" />
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue';

export default {
  name: 'App',
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodo: '',
      todos: [
        { title: 'Buy groceries', completed: false },
        { title: 'Finish project', completed: true },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({ title: this.newTodo, completed: false });
        this.newTodo = '';
      }
    },
    updateTodo(index, completed) {
      this.todos[index].completed = completed;
    },
  },
};
</script>

<style>
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f5f5f5;
}

#app {
  max-width: 500px;
  margin: 50px auto;
  padding: 20px;
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
}

h1 {
  font-size: 24px;
  font-weight: bold;
  color: #333333;
  margin-bottom: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 0 0 20px 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 12px;
  background-color: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 4px;
  margin-bottom: 10px;
}

.add-todo {
  width: 100%;
  padding: 8px 12px;
  box-sizing: border-box;
  border: 1px solid #cccccc;
  border-radius: 4px;
  font-size: 16px;
}
.completed {
  text-decoration: line-through;
  color: #adb5bd;
}
</style>


