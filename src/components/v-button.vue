<template>
  <button type="button" class="button">
    {{ buttonText }}
    <img :src="iconPath" />
  </button>
</template>

<script>
export default {
  props: {
    iconPath: {
      type: String,
      required: true,
    },
  },
};
</script>
