<template>
  <div class="box" :class="{ reversed, filled, first }">
    <div class="text">
      <div class="ct">
        <div class="title">{{ title }}</div>
        <div v-if="subtitle" class="subtitle">{{ subtitle }}</div>
        <div class="desc">
          <i18n :path="descTranslationKey" tag="span">
            <template #br>
              <br />
            </template>
            <template #email>
              <a href="mailto:info@marvlukocht.it" class="clickable underline"
                >info@marvlukocht.it</a
              >
            </template>
            <template #phone>
              <a href="tel:+393405947912" class="clickable underline"
                >+39 340 59 47 912</a
              >
            </template>
          </i18n>
        </div>
      </div>
    </div>
    <div class="image">
      <div
        class="img"
        :style="{ backgroundImage: 'url(/image/home/' + imgName + '.jpeg)' }"
      ></div>
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
      default: null,
    },
    descTranslationKey: {
      type: String,
      required: true,
    },
    imgName: {
      type: String,
      required: true,
    },
    reversed: {
      type: Boolean,
      default: false,
    },
    filled: {
      type: Boolean,
      default: false,
    },
    first: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="postcss" scoped>
.box {
  @apply flex flex-row justify-center py-16;

  & .text {
    @apply flex-1;

    & .ct {
      @apply pt-8 px-3 text-right;

      & .title {
        @apply text-5xl uppercase text-primary font-bold mb-6;
      }

      & .subtitle {
        @apply text-base text-secondary uppercase font-semibold mb-1;
      }

      & .desc {
        @apply text-base font-light text-secondary;
      }
    }
  }

  & .image {
    @apply flex-1;

    & .img {
      @apply bg-cover bg-center bg-no-repeat bg-placeholder;

      padding-top: 120%;
    }
  }

  &.filled {
    @apply items-center;

    & .text {
      & .ct {
        @apply bg-primary pb-12;

        & .title,
        & .subtitle,
        & .desc {
          @apply text-white;
        }
      }
    }
  }
}

@media only screen and (min-width: 981px) {
  .box {
    & .text {
      & .ct {
        & .title {
          @apply relative -mr-36;
        }
      }
    }

    &.reversed {
      @apply flex-row-reverse;

      & .text {
        & .ct {
          @apply text-left;

          & .title {
            @apply relative -ml-36 mr-0;
          }
        }
      }
    }

    &.filled {
      & .text {
        & .ct {
          @apply pl-24;

          & .title {
            @apply -mr-24;
          }
        }
      }
    }
  }
}

@media only screen and (max-width: 980px) {
  .box {
    @apply flex-col-reverse pb-0;

    & .text {
      & .ct {
        @apply text-left px-6;

        & .title {
          @apply text-4xl;
        }
      }
    }

    & .image {
      @apply w-full;
    }

    &.first {
      @apply flex-col pb-14;

      & .image {
        & .img {
          @apply ml-6 mr-6 -mt-6;
        }
      }
    }
  }
}
</style>
