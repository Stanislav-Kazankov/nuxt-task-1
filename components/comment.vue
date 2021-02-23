<template>
  <tr class="comment">
    <td class="cell"
      v-for="(value, index) of values"
      :key="index"
  >
      {{value}}
    </td>
    <td class="cell">
      <button class="button"
        type="button"
        @click="onBtnClick"
      >
        Удалить комментарий
      </button>
    </td>
  </tr>
</template>

<script>
  export default {
    props: {
      comment: Object,
    },
    methods: {
      onBtnClick() {
        this.$emit('commentdelete');
      }
    },
    computed: {
      values() {
        return Object.values(this.comment);
      },
    },
  }
</script>