<template>
  <header class="header">
    <div class="header__container container">
      <slot name="header"></slot>
    </div>
  </header>
  <aside class="aside">
    <slot name="aside"></slot>
  </aside>
  <main class="main">
    <div class="main__container container">
      <slot name="main"></slot>
    </div>
  </main>
  <footer class="footer">
    <div class="footer__container container">
      <slot name="footer"></slot>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'default-layout',
};
</script>

<style>
.container {
  max-width: 100%;
  padding: 0 100px;
  margin: 0 auto;
}
</style>
