<template>
  <default-layout>
    <template v-slot:header>
      <header></header>
    </template>
    <template v-slot:aside>
      <aside></aside>
    </template>
    <template v-slot:main>
      <main></main>
    </template>
    <template v-slot:footer>
      <footer></footer>
    </template>
  </default-layout>
</template>

<script>
import defaultLayout from './components/default-layout.vue';

export default {
  name: 'App',
  components: {
    defaultLayout,
  },
};
</script>
