<template>
  <div class="control-panel">
    <input class="control-panel__field"
      type="text"
      name="todo"
      placeholder="Напишите задачу.."
      v-model:value="addedTask.title"
    >
    <button type="button"
      @click="onBtnClick"
    >
    Добавить задачу
    </button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        addedTask: {
          isDone: false,
          title: '',
        },
      }
    },
    methods: {
      onBtnClick() {
        this.$root.$emit('taskadd', {...this.addedTask});
      }
    }
  }
</script>

<style lang="scss" scoped>
  .control-panel {
    display: flex;
    flex-wrap: wrap;

    &__field {
      margin-right: 10px;
    }
  }
</style>