<template>
  <header>
    <slot name="header"></slot>
  </header>
  <aside>
    <slot name="aside"></slot>
  </aside>
  <main>
    <slot name="main"></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</template>

<script>
export default {
  name: 'default-layout',
};
</script>
