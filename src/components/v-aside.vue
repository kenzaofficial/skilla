<template>
  <img src="../assets//svg/logo.svg" width="109" height="28" class="logo" />
  <v-main-nav></v-main-nav>
</template>

<script>
import VMainNav from '@/components/v-main-nav.vue';
export default {
  components: {
    VMainNav,
  },
};
</script>

<style>
.aside {
  position: relative;
  grid-row: 1/3;
  padding: 20px 0;
  max-width: 240px;
  width: 100%;
  background-color: #091336;
  order: -1;
}

.logo {
  padding: 0 14px;
}
</style>
