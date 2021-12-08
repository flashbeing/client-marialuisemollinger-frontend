<template>
  <header>
    <div class="center">
      <nuxt-link :to="localePath('/')">
        <Icon name="logo" class="logo" />
      </nuxt-link>
      <div class="lang-selector">
        <nuxt-link
          class="language cursor-pointer"
          to="/"
          :class="{ underline: $i18n.locale === 'de' }"
          >DE</nuxt-link
        >
        •
        <nuxt-link
          class="language cursor-pointer"
          to="/it/"
          :class="{ underline: $i18n.locale === 'it' }"
          >IT</nuxt-link
        >
      </div>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style lang="postcss" scoped>
header {
  @apply absolute font-semibold select-none top-0 left-0 right-0;

  & .logo {
    @apply relative z-20;

    height: 120px;
    margin-top: 40px;
  }

  & .lang-selector {
    @apply relative float-right mt-12 text-lg text-white z-20;
  }
}

@media only screen and (max-width: 980px) {
  header {
    @apply ml-6;

    & .logo {
      @apply mt-6;

      height: 80px;
    }

    & .lang-selector {
      @apply mr-6;
    }
  }
}
</style>
