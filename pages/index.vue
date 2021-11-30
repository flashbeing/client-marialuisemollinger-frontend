<template>
  <main>
    <section class="center">
      <div class="center">
        <ElementsGrid
          image="Portrait_Marialuise_DEF@2x.png"
          :title="$t('page.homepage.firstSection.elements.first.title')"
          :has-background="true"
        >
          {{$t('page.homepage.firstSection.elements.first.content')}}
        </ElementsGrid>
      </div>
    </section>
    <section class="center">
      <FaqItem content="dadadasdsad" title="testing the tester tested"></FaqItem>
    </section>
  </main>
</template>

<script>
export default {}
</script>
<style lang="postcss" scoped>
main {
  & .elements {
    @apply flex flex-col space-y-10;
  }
}
</style>
