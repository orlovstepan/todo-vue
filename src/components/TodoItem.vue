<template>
  <div class="todo-item">
    <input type="checkbox" :checked="completed" @change="toggleCompleted" />
    <label>{{ title }}</label>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['title', 'completed'],
  methods: {
    toggleCompleted() {
      this.$emit('update:completed', !this.completed);
    },
  },
};
</script>

<style scoped>
input[type='checkbox'] {
  margin-right: 10px;
}
</style>


