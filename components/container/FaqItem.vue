<template>
  <div class="faq">
    <div class="title clickable" @click="toggle">
      <div class="text">
        <h2>{{ title }}</h2>
      </div>
      <div class="arrow" :class="+isExpanded ? 'up' : 'down'"></div>
    </div>
    <div
      v-show="isExpanded"
      class="desc"
    >
      <p>{{content}}</p>
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
    content: {
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
  @apply p-3;

  background-color: #F5F7F5;
  & .title {
    @apply text-lg select-none flex items-center justify-between px-2;

    & .text {
      @apply select-none flex-grow;

      max-width: calc(100% - 20px);

      & h2 {
        @apply font-medium text-base;
      }
    }

    & .arrow {
      @apply inline-block transition-transform duration-200;

      border: solid #386A47;
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
    @apply pt-1 pl-2;

    & p {
      @apply whitespace-pre-line m-auto pt-6;

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
