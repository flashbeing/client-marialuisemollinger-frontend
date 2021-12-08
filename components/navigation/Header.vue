<template>
  <header>
    <div class="center">
      <nuxt-link :to="localePath('/')">
        <Icon name="logo" class="logo" />
      </nuxt-link>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style lang="postcss" scoped>
header {
  @apply font-semibold select-none relative top-0 left-0 right-0;

  height: 800px;

  & .logo {
    @apply relative z-20;

    height: 120px;
    margin-top: 20px;
  }
}
</style>
