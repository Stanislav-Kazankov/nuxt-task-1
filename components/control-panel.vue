<template>
  <article class="control-panel">
    <h3 class="control-panel__title">Панель добавления задачи</h3>
    <input class="control-panel__field"
      id="field"
      type="text"
      name="todo"
      placeholder="Напишите задачу.."
      v-model:value="addedTask.title"
    >
    <label class="control-panel__caption"
      for="field"
    >
      Поле для ввода новой задачи
    </label>
    <button type="button"
      @click="onBtnClick"
    >
    Добавить задачу
    </button>
  </article>
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
  @import "@/assets/sass/mixins.scss"

  .control-panel {
    display: flex;
    flex-wrap: wrap;

    &__title,
    &__caption {
      @include visually-hidden();
    }

    &__field {
      margin-right: 10px;
    }
  }
</style>