<template>
  <v-main
  >
    <v-container
      class="mx-auto pt-0"
      :style="`max-width:${ maxwidthContainer }`"
    >
      <slot />
    </v-container>
  </v-main>
</template>

<script>
export default {
  name: 'InternaMain',

  props: {
    maxwidthContainer: {
      type: String,
      default: '1200px',
    },
    rodape: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
