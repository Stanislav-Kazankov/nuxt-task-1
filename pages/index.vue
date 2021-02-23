<template>
  <div class="page">
    <div class="page__centerer">
      <div class="page__app page__app--todos">
        <h1 class="page__h1">
          To do list
        </h1>
        <control-panel />
        <todo-list :tasks="tasks"/>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        tasks: [
          {
            isDone: false,
            title: 'Сходить в кино',
          },
          {
            isDone: true,
            title: 'Погулять с собакой',
          },
          {
            isDone: false,
            title: 'Встретится с Шерлоком на Бэйкер Стрит',
          },
        ],
      }
    },
  }
</script>

<style lang="scss" scoped>
  .page__app {
    justify-content: center;

    text-align: left;

    &--todos {
      padding-left: 20px;
      padding-right: 20px;
      padding-top: 20px;
      padding-bottom: 35px;
      width: 500px;
      min-height: 323px;

      font-size: 14px;
      line-height: 16px;

      border: 2px solid red;
      border-radius: 20px;

      .control-panel {
        margin-bottom: 30px;
      }

      .todo-list {
        margin-left: 20px;
      }
    }
  }
</style>
