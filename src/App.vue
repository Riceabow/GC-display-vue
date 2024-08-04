<template>
    <Page1 />
    <Page2 />
    <Page3 />
</template>

<script>
import Page1 from './views/Page1.vue'
import Page2 from './views/Page2.vue'
import Page3 from './views/Page3.vue';
export default {
  name: 'App',
  components: {
    Page1,
    Page2,
    Page3
  }
}
</script>

<style>
@import './assets/style/style.css';
</style>
