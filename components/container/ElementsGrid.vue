<template>
<div class="main-container" :class="{'is-reverse': reverseBackground}">
  <div class="text-box" :class="{'has-background': hasBackground}">
    <div class="text">
      <h3 v-if="subtitle" class="font-black">{{subtitle}}</h3>
      <slot />
    </div>
  </div>
  <div class="image" :style="boxImage" />
</div>
</template>

<script>
export default {
  name: "ElementsGrid",
  props:{
    title: {
      type: String,
      required: true
    },
    image: {
      type: String,
      required: true
    },
    hasBackground: {
      type: Boolean,
      default: false
    },
    reverseBackground: {
      type: Boolean,
      default: false
    },
    subtitle: {
      type: String,
      default: ''
    }
  },
  computed: {
    boxImage() {
      return {
        backgroundImage: 'url(/image/' + this.image + ')',
      }
    }
  }
}
</script>

<style lang="postcss" scoped>
.main-container {
  @apply flex flex-row;

  height: 370px;

  & .text-box {
    @apply flex justify-end items-center text-right my-12;

    width: 420px;

    & .text {
      @apply text-black pr-5 space-y-5;

      width: 80%;
    }

    &.has-background {
      @apply bg-primary;

      & .text {
        @apply text-white;
      }
    }
  }

  &.is-reverse {
    @apply flex-row-reverse;

    & .text-box {
      @apply text-left justify-start;

      & .text {
        @apply pr-0 pl-5;
      }
    }
  }

  & .image {
    @apply bg-cover bg-center;

    width: 400px;
    height: auto;
  }
}
@media only screen and (max-width: 980px){
  .main-container {
    @apply flex-col;

    height: auto;

    & .text-box {
      @apply flex justify-end items-center text-right p-5;

      width: 100%;

      & .text {
        @apply pr-0 space-y-5;

        width: 100%;

        & h2 {
          @apply font-bold relative;

          font-size: 35px;
          left: auto;
        }
      }
    }

    & .image {
      @apply bg-cover bg-center relative;

      width: auto;
      height: 200px;
      top: -11%;
      margin-right: 25px;
      margin-left: 25px;
    }

    &.is-reverse {
      @apply flex-col-reverse;

      & .text-box {
        @apply text-current justify-center;

        & .text {
          @apply pr-0 pl-5;
        }
      }

      & .image {
        top: auto;
      }
    }
  }
}
</style>
