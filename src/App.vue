<template>
  <default-layout>
    <template v-slot:header>
      <v-header></v-header>
    </template>
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
import VHeader from './components/v-header.vue';

export default {
  name: 'App',
  components: {
    defaultLayout,
    VAside,
    VHeader,
  },
};
</script>

<style>
body {
  margin: 0;
}

#app {
  width: 100%;
  display: flex;
}
</style>
