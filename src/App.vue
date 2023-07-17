<script>
import ProjectList from './components/ProjectList.vue';

export default {
  components: {
    ProjectList,
  }
};
</script>

<template>
  <header class="bg-dark py-3">
    <div class="container">
      <h1 class="text-center text-primary">Boolean Projects Git Hub</h1>
    </div>
  </header>
  <ProjectList />
</template>

<style lang="scss">
@import 'bootstrap/scss/bootstrap';
</style>
