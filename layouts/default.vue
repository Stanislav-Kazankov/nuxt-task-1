<template>
  <div class="default">
    <header class="default__header">
      <div class="default__centerer">
        <navbar :itemData="itemData"/>
      </div>
    </header>
    <main class="default__main">
      <nuxt />
    </main>
    <footer class="default__footer">
      <div class="default__centerer">
        <p class="default__p">
          Дизайн и фронтенд данного сайта выполнены мной.
          © Все права защищены.
        </p>
      </div>
    </footer>
  </div>
</template>

<script>
  import navbar from '@/components/navbar';

  export default {
    data() {
      return {
        itemData: [
          {
            url: '/',
            caption: 'To do list',
          },
          {
            url: '/fetch',
            caption: 'Fetch',
          },
          {
            url: '/vee-validate',
            caption: 'Vee-validate',
          },
        ],
      }
    },
    components: {
      navbar
    },
  }
</script>

<style lang="scss" scoped>
  @import "@/assets/sass/mixins.scss";

  .default {
    display: grid;
    grid-template-rows: min-content 1fr min-content;
    min-height: 100vh;

    &__centerer {
      @include make-centerer();
    }
    
    &__header {
      @include make-gradient(
        #a1a31a,
        #ffffff00,
        60%
      );
    }

    &__main {
      @include make-gradient(
        #ffffff00,
        #a1a31a,
        60%
      );
    }

    &__footer {
      padding-top: 30px;
      padding-bottom: 36px;
    }

    &__p {
      width: 500px;

      font-size: 20px;
      line-height: 26px;
    }
  }
</style>