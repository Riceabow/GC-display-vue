<template>
    <Page1 />
    <Page2 />
    <Page3 />
    <Page4 />
    <Page5 />
    <!-- <noodle /> -->
    <Page6 />

</template>

<script>
import Page1 from './views/Page1.vue'
import Page2 from './views/Page2.vue'
import Page3 from './views/Page3.vue';
import Page5 from './views/Page5.vue';
import Page6 from './views/Page6.vue';
import noodle from './components/noodle.vue';
import Page4 from './views/Page4.vue';
export default {
  name: 'App',
  components: {
    Page1,
    Page2,
    Page3,
    Page4,
    Page5,
    noodle,
    Page6
  }
}
</script>

<style>
@import './assets/style/style.css';
</style>./views/Page5.vue
