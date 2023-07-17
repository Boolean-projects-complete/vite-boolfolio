<script>
import AppHeader from './components/AppHeader.vue';
import AppNav from './components/AppNav.vue';
import AppFooter from './components/AppFooter.vue'

export default {
  components: {
    AppNav,
    AppFooter,
    AppHeader,
  }
};
</script>

<template>
  <header>
    <AppHeader />
    <AppNav />
  </header>

  <div class="container_main">
    <router-view></router-view>
  </div>

  <AppFooter />
</template>

<style lang="scss">
@import 'bootstrap/scss/bootstrap';
</style>
