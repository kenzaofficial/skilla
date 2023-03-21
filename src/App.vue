<template>
  <default-layout>
    <template v-slot:header>
      <v-header></v-header>
    </template>
    <template v-slot:aside>
      <v-aside></v-aside>
    </template>
    <template v-slot:main>
      <div class="upper-row">
        <v-balance></v-balance>
        <v-calendar-button></v-calendar-button>
      </div>
      <v-filter-row></v-filter-row>
    </template>
    <template v-slot:footer></template>
  </default-layout>
</template>

<script>
import VAside from './components/v-aside.vue';
import defaultLayout from './components/default-layout.vue';
import VHeader from './components/v-header.vue';
import VFilterRow from './components/v-filter-row.vue';
import VBalance from './components/v-balance.vue';
import VCalendarButton from './components/v-calendar-button.vue';

export default {
  name: 'App',
  components: {
    defaultLayout,
    VAside,
    VHeader,
    VFilterRow,
    VBalance,
    VCalendarButton,
  },
};
</script>

<style>
body {
  margin: 0;
}

.app {
  height: 100vh;
  display: grid;
  grid-template-columns: 240px auto;
  grid-template-rows: auto 1fr;
}

.main {
  padding: 20px 0;
  background-color: #f1f4f9;
  grid-row: 2/2;
  grid-column: 2/-1;
}

.upper-row {
  display: flex;
  column-gap: 50px;
  margin-bottom: 20px;
}
</style>
