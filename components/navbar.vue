<template>
  <ul class="navbar">
    <li class="navbar__item"
      v-for="(item, index) of itemData"
      :key="index">
      <nuxt-link
        class="navbar__link"
        :to="item.url"
        active-class="is-active"
        exact
        :prefetch="false"
      >
        {{item.caption}}
      </nuxt-link>
    </li>
  </ul>
</template>

<script>
  export default {
    props: {
      itemData: Array,
    }
  }
</script>

<style lang="scss" scoped>
  @import "@/assets/sass/mixins.scss";

  .navbar {
    display: flex;
    flex-wrap: wrap;
    padding-left: 0;
    padding-top: 30px;
    padding-bottom: 26px;

    list-style: none;

    margin-right: -60px;

    &__item {
      max-width: 200px;

      margin-right: 60px;
      margin-bottom: 10px;
    }

    &__link {
      border-top-left-radius: 15px;
      border-top-right-radius: 15px;
    }
  }

  .is-active {
    @include make-gradient(
      #ffffff00,
      #a1a31a,
      100%
    );
  }
</style>