<template>
  <div class="title" :class="{ 'expanded-title': expandedTitle }">
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
    expandedTitle: {
      type: Boolean,
      default: false,
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
        @apply pl-16 pr-72 py-10 text-5xl font-bold uppercase bg-primary;
      }
    }

    &.subtitle {
      & p {
        @apply mt-6 -ml-48 py-10 px-24 text-base text-white;

        background: #44694a;
      }
    }
  }
}

@media only screen and (min-width: 981px) {
  .title {
    &.expanded-title {
      & .box {
        @apply text-white;

        &.main {
          & h2 {
            @apply pr-12 py-16;

            width: 650px;
          }
        }

        &.subtitle {
          & p {
            @apply mt-10 -ml-14 py-6 px-4;
          }
        }
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
          @apply pb-16 text-4xl;
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
