<template>
  <svg
    :class="className"
    xmlns="http://www.w3.org/2000/svg">
    <title v-if="title">{{ title }}</title>
    <use
      :xlink:href="iconPath"
      xmlns:xlink="http://www.w3.org/1999/xlink"></use>
  </svg>
</template>

<script>
export default {
  name: 'SvgIcon',

  props: {
    name: {
      type: String,
      required: true,
    },

    title: {
      type: String,
      default: null,
    },
  },

  computed: {
    iconPath() {
      let icon = require(`@/assets/icons/${this.name}.svg`); // eslint-disable-line
      if (Object.prototype.hasOwnProperty.call(icon, 'default')) {
        icon = icon.default;
      }

      return icon.url;
    },

    className() {
      return `svg-icon svg-icon--${this.name}`;
    },
  },
};
</script>

<style lang="scss">
  .svg-icon {
    fill: currentColor;
    @include size(24px);
  }
</style>
