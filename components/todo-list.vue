<template>
  <ul class="todo-list">
    <task
      v-for="(task, index) in tasks"
      :key="index"
      :task="task"
      @taskdelete="onTaskDelete(index)"
    />
  </ul>
</template>

<script>
  export default {
    props: {
      tasks: Array,
    },
    methods: {
      onTaskDelete(taskIndex) {
        this.tasks.splice(taskIndex, 1);
      }
    },
    created() {
      this.$root.$on('taskadd', (addedTask) => {
        this.tasks.push(addedTask);
      })
    }
  }
</script>

<style lang="scss" scoped> 
  .todo-list {
    padding: 0;
    list-style: none;

    .task {
      margin-bottom: 20px;
    }
  }
</style>