<template>
  <div class="faq">
    <div class="title clickable" @click="toggle">
      <div class="text">
        <h2>{{ title }}</h2>
      </div>
      <div class="arrow" :class="+isExpanded ? 'up' : 'down'"></div>
    </div>
    <div v-show="isExpanded" class="desc">
      <i18n :path="descTranslationKey" tag="p">
        <template #br>
          <br />
        </template>
        <template #email>
          <a href="mailto:info@marylukocht.it" class="clickable underline"
            >info@marylukocht.it</a
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
</template>
<script>
export default {
  name: 'FaqItem',

  props: {
    title: {
      type: String,
      required: true,
    },
    descTranslationKey: {
      type: String,
      required: true,
    },
  },

  data() {
    return {
      isExpanded: false,
    }
  },
  methods: {
    toggle() {
      this.isExpanded = !this.isExpanded
    },
  },
}
</script>

<style lang="postcss" scoped>
.faq {
  @apply py-3 px-5 bg-light-green;

  & .title {
    @apply text-lg select-none flex items-center justify-between;

    & .text {
      @apply select-none flex-grow;

      max-width: calc(100% - 20px);

      & h2 {
        @apply font-medium text-base text-secondary;
      }
    }

    & .arrow {
      @apply inline-block transition-transform duration-200;

      border: solid #386a47;
      border-width: 0 3px 3px 0;
      padding: 3px;

      &.down {
        transform: rotate(45deg);
      }

      &.up {
        transform: rotate(-135deg);
      }
    }
  }

  & .desc {
    @apply pt-3;

    & p {
      @apply whitespace-pre-line m-auto mx-0 font-light text-secondary;

      max-width: 90%;
    }
  }
}

@media only screen and (max-width: 980px) {
  .faq {
    & .title {
      @apply px-0;
    }
  }
}
</style>
