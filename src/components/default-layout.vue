<template>
  <header class="header">
    <div class="header__container container">
      <slot name="header"></slot>
    </div>
  </header>
  <aside class="aside">
    <slot name="aside"></slot>
  </aside>
  <main>
    <slot name="main"></slot>
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
  display: flex;
  align-items: center;
  max-width: 100%;
  padding: 0 15px;
  margin: 0 auto;
}
</style>
