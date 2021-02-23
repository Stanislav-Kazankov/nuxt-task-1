
<template>
  <li class="task">
    <input class="task__checkbox"
      type="checkbox"
      name="task"
      v-model:checked="task.isDone"
    >
    <span class="task__title">{{task.title}}</span>
    <button
      class="task__button"
      type="button"
      @click="onBtnClick"
    >
        Удалить задачу
    </button>
  </li>
</template>

<script>
  export default {
    props: {
      task: Object,
    },
    methods: {
      onBtnClick() {
          this.$emit('taskdelete')
      }
    }
  }
</script>

<style lang="scss" scoped>
  .task {
    display: flex;
    align-items: center;
    min-height: 30px;
    
    &:last-child {
      margin-bottom: 0;
    }
    
    &__checkbox {
      margin-right: 10px;

      &:checked {
        ~ .task__title {
          text-decoration: line-through;
        }
        
        ~ .task__button {
          display: none;
        }
      }
    }
    
    &__title {
      width: 200px;
      text-align: left;

      margin-right: auto;
    }
  }
</style>