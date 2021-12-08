<template>
  <div class="title">
    <div class="box main">
      <h2>{{ title }}</h2>
    </div>
    <div class="box subtitle">
      <p>{{ subtitle }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      required: true,
    },
  },
}
</script>

<style lang="postcss" scoped>
.title {
  @apply flex flex-row;

  & .box {
    @apply text-white;

    &.main {
      & h2 {
        @apply pl-16 pr-32 py-10 text-4xl font-bold uppercase bg-primary;
      }
    }

    &.subtitle {
      & p {
        @apply mt-10 -ml-16 py-10 px-24 text-base text-white;

        background: #44694a;
      }
    }
  }
}

@media only screen and (max-width: 980px) {
  .title {
    @apply flex-col;

    & .box {
      &.main {
        & h2 {
          @apply pb-16;
        }
      }

      &.subtitle {
        & p {
          @apply -mt-10 ml-16 px-6;
        }
      }
    }
  }
}
</style>
