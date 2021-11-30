<template>
  <header>
    <div class="center">
      <nuxt-link :to="localePath('/')" :title="$t('common.homepage')">
        <Icon name="logo" class="logo" />
      </nuxt-link>
    </div>
    <iframe class="video" src="https://www.youtube.com/embed/OhBo1A8atuA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />
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

  & .video {
    @apply w-full z-10 top-0 left-0 right-0 absolute;

    height: 720px;
  }

}
</style>
