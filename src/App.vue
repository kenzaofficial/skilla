<template>
  <default-layout>
    <template v-slot:header></template>
    <template v-slot:aside>
      <v-aside></v-aside>
    </template>
    <template v-slot:main></template>
    <template v-slot:footer></template>
  </default-layout>
</template>

<script>
import VAside from './components/v-aside.vue';
import defaultLayout from './components/default-layout.vue';

export default {
  name: 'App',
  components: {
    defaultLayout,
    VAside,
  },
};
</script>

<style>
body {
  margin: 0;
}

.aside {
  background-color: #091336;
  max-width: 240px;
}
</style>
