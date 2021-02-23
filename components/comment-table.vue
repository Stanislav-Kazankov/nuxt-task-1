<template>
  <table class="comment-table">
    <thead>
      <tr>
        <th class="cell"
          v-for="(columnTitle, index) of columnTitles"
          :key="index"
        >
        {{columnTitle}}
        </th>
        <th class="cell"></th>
      </tr>
    </thead>
    <tbody>
      <comment 
        v-for="(comment, index) of comments"
        :key="index"
        :comment="comment"
        @commentdelete="onCommentDelete(index)"
      />
    </tbody>
  </table>
</template>

<script>
  export default {
    props: {
        comments: Array,
    },
    methods: {
        onCommentDelete(commentIndex) {
        this.comments.splice(commentIndex, 1);
        }
    },
    computed: {
      columnTitles() {
        let result = [];
        if (this.comments.length) {
            result = Object.keys(this.comments[0]);
        }
        return result;
      },
    },
  }
</script>

<style lang="scss" scoped>
  .comment-table {
    border-collapse: collapse;

    font-family: 'Times New Roman', serif;
    font-size: 16px;
    line-height: 18px;
    color: black;

    margin-top: 20px;
  }
</style>