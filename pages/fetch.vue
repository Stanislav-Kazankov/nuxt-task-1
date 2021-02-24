<template>
  <div class="page">
    <div class="page__centerer">
      <div class="page__app page__app--fetch">
        <h1 class="page__h1">
          Fetch
        </h1>
        <div>
          <button class="button"
            type="button"
            :style="{
            'cursor': isLoading ?
                'wait' : 'pointer'
            }"
            @click="onBtnClick"
          >
            Загрузить комментарии
          </button>
          <transition name="fade">
            <comment-table
              :comments="comments"
            />
          </transition>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    async asyncData({$axios}) {
      const comments = await $axios.$get(process.env.commentUrl);
      
      return {comments};
    },
    data: () => ({
      comments: [],
      isLoading: false,
    }),
    methods: {
      onBtnClick() {
        this.comments = [];
        this.isLoading = true;
        const whenCommentsLoaded = this.$axios
          .get(process.env.commentUrl);

        whenCommentsLoaded.then((response) => {
          this.comments = response.data;
        })
        .catch(({response}) => {
          if (response) {
            alert(
              'При попытке получить данные с сервера произошла ошибка ' +
              response.status
            );
          }
        })
        .finally((response) => {
          this.isLoading = false;
        })
      },
    },
  }
</script>

<style lang="scss" scoped>
  @import "@/assets/sass/mixins.scss";

  .page__app--fetch {
    justify-items: center;

    .button {
      margin: auto 100px;
    }
  }

  .fade {
    @include make-fade(1s);
  }
</style>