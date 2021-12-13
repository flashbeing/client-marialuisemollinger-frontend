<template>
  <main>
    <div class="cover">
      <div class="desktop-only">
        <video
          ref="desktopVideo"
          :class="{ 'show-video': desktopVideoVisible }"
          :src="desktopVideoUrl + '#t=0.001'"
          preload="metadata"
          @click="pauseVideoPlayback('desktopVideo')"
        ></video>
        <div
          v-if="!desktopVideoVisible"
          class="play-bt clickable"
          @click="startVideoPlayback('desktopVideo')"
        >
          <div class="ico-ct">
            <Icon name="play" />
          </div>
        </div>
      </div>
      <div class="mobile-only">
        <video
          ref="mobileVideo"
          :class="{ 'show-video': mobileVideoVisible }"
          :src="mobileVideoUrl + '#t=0.001'"
          preload="metadata"
          @click="pauseVideoPlayback('mobileVideo')"
        ></video>
        <div
          v-if="!mobileVideoVisible"
          class="play-bt clickable"
          @click="startVideoPlayback('mobileVideo')"
        >
          <div class="ico-ct">
            <Icon name="play" />
          </div>
        </div>
      </div>
    </div>
    <section class="main-features center compact">
      <FeatureBox
        img-name="marialuise"
        :title="$t('page.home.features.hello.title')"
        desc-translation-key="page.home.features.hello.desc"
        filled
        first
      />
      <FeatureBox
        img-name="home-cook"
        :title="$t('page.home.features.homeCook.title')"
        :subtitle="$t('page.home.features.homeCook.subtitle')"
        desc-translation-key="page.home.features.homeCook.desc"
        reversed
      />
      <FeatureBox
        img-name="private-event"
        :title="$t('page.home.features.privateEvent.title')"
        :subtitle="$t('page.home.features.privateEvent.subtitle')"
        desc-translation-key="page.home.features.privateEvent.desc"
      />
      <FeatureBox
        img-name="business-event"
        :title="$t('page.home.features.businessEvent.title')"
        :subtitle="$t('page.home.features.businessEvent.subtitle')"
        desc-translation-key="page.home.features.businessEvent.desc"
        reversed
      />
      <FeatureBox
        img-name="specs"
        :title="$t('page.home.features.specs.title')"
        :subtitle="$t('page.home.features.specs.subtitle')"
        desc-translation-key="page.home.features.specs.desc"
      />
    </section>
    <section class="faqs center compact">
      <SectionTitle
        :title="$t('page.home.faq.title')"
        :subtitle="$t('page.home.faq.subtitle')"
        class="mb-16"
      />
      <FaqItem
        v-for="faq in faqs"
        :key="faq.title"
        :title="faq.title"
        :desc-translation-key="faq.descTranslationKey"
        class="faq"
      ></FaqItem>
    </section>
    <!--<section class="instagram center compact">
      <h2>Instagram</h2>
      <div class="elfsight-app-559f950b-6747-4c7c-803a-1086ceb3acd7"></div>
    </section>-->
    <section class="contact center compact">
      <div>
        <SectionTitle
          :title="$t('page.home.contact.title')"
          :subtitle="$t('page.home.contact.subtitle')"
          :expanded-title="true"
        />
      </div>
      <form>
        <div>
          <TextArea
            v-model="contactForm.message"
            :placeholder="$t('page.home.contact.message')"
            aspect="fill"
            class="mb-6"
          />
        </div>
        <div class="inputs">
          <div>
            <TextInput
              v-model="contactForm.surname"
              :placeholder="$t('page.home.contact.surname')"
              aspect="fill"
            />
          </div>
          <div>
            <TextInput
              v-model="contactForm.name"
              :placeholder="$t('page.home.contact.name')"
              aspect="fill"
            />
          </div>
          <div>
            <TextInput
              v-model="contactForm.email"
              :placeholder="$t('page.home.contact.email')"
              aspect="fill"
            />
          </div>
          <div>
            <Button
              :value="
                sentMessage
                  ? $t('page.home.contact.sentThanks')
                  : $t('page.home.contact.send')
              "
              :loading="sendingMessage"
              :disabled="sentMessage || !completedFields"
              aspect="fill"
              @click="sendMessage"
            />
          </div>
        </div>
        <div>
          <Checkbox
            v-model="contactForm.terms"
            :label="$t('page.home.contact.iAcceptPrivacyPolicy')"
          />
        </div>
      </form>
    </section>
  </main>
</template>

<script>
import { EMAIL_TOKEN } from '~/config.json'

export default {
  data() {
    return {
      sendingMessage: false,
      sentMessage: false,
      contactForm: {
        message: '',
        surname: '',
        name: '',
        email: '',
        terms: false,
      },
      desktopVideoVisible: false,
      mobileVideoVisible: false,
    }
  },

  head() {
    return {
      script: [
        {
          src: 'https://apps.elfsight.com/p/platform.js',
          defer: true,
        },
      ],
    }
  },

  computed: {
    faqs() {
      return [
        this.getFaqItem('intolerance'),
        this.getFaqItem('kitchenSize'),
        this.getFaqItem('cost'),
        this.getFaqItem('buySpices'),
        this.getFaqItem('choose'),
        this.getFaqItem('maxPeople'),
        this.getFaqItem('decoration'),
        this.getFaqItem('partner'),
        this.getFaqItem('breakfast'),
        this.getFaqItem('drinks'),
        this.getFaqItem('cleanup'),
        this.getFaqItem('catering'),
        this.getFaqItem('otherQuestions'),
      ]
    },

    completedFields() {
      // eslint-disable-next-line no-unused-vars
      for (const [_, value] of Object.entries(this.contactForm)) {
        if (!value) {
          return false
        }
      }

      return true
    },

    desktopVideoUrl() {
      return this.$i18n.locale === 'it'
        ? 'https://codeworks-clients-public.s3.eu-west-1.amazonaws.com/marialuisemollinger/desktop-video-it.mp4'
        : 'https://codeworks-clients-public.s3.eu-west-1.amazonaws.com/marialuisemollinger/desktop-video-de.mp4'
    },

    mobileVideoUrl() {
      return this.$i18n.locale === 'it'
        ? 'https://codeworks-clients-public.s3.eu-west-1.amazonaws.com/marialuisemollinger/mobile-video-it.mp4'
        : 'https://codeworks-clients-public.s3.eu-west-1.amazonaws.com/marialuisemollinger/mobile-video-de.mp4'
    },
  },

  methods: {
    getFaqItem(id) {
      return {
        title: this.$t('page.home.faq.faqs.' + id + '.title'),
        descTranslationKey: 'page.home.faq.faqs.' + id + '.desc',
      }
    },

    startVideoPlayback(videoType) {
      this[videoType + 'Visible'] = true
      this.$refs[videoType].play()
    },

    pauseVideoPlayback(videoType) {
      this[videoType + 'Visible'] = false
      this.$refs[videoType].pause()
    },

    sendMessage() {
      this.sendingMessage = true
      this.$axios
        .post('/em/', {
          t: EMAIL_TOKEN,
          d: this.contactForm,
        })
        .then(
          (response) => {
            if (response.data && response.data.status === 1) {
              this.sendingMessage = false
              this.sentMessage = true
              this.resetFields()
            } else {
              this.notifyError()
            }
          },
          () => {
            this.notifyError()
          }
        )
    },

    notifyError() {
      this.sendingMessage = false
      alert(this.$t('globals.genericError'))
    },

    resetFields() {
      const setForm = { ...this.contactForm }

      for (const [fieldId, value] of Object.entries(this.contactForm)) {
        setForm[fieldId] = value === true ? false : ''
      }

      this.contactForm = setForm
    },
  },
}
</script>

<style lang="postcss" scoped>
h2 {
  @apply text-4xl text-primary text-center uppercase font-bold;
}

.cover {
  @apply relative bg-cover bg-center bg-no-repeat bg-placeholder;

  height: 56vw;

  & video {
    @apply w-full h-full cursor-pointer;
  }

  & .play-bt {
    @apply absolute bg-primary cursor-pointer;

    width: 90px;
    height: 90px;
    top: 50%;
    left: 50%;
    margin-top: -45px;
    margin-left: -45px;
    border-radius: 50%;

    & .ico-ct {
      @apply flex w-full h-full items-center justify-center;

      & svg {
        width: 40px;
        fill: theme(colors.white);
      }
    }
  }
}

section {
  @apply my-10;

  &.main-features {
    @apply mb-20;
  }

  &.instagram {
    @apply py-24;

    & h2 {
      @apply mb-8;
    }
  }

  &.faqs {
    @apply mb-32; /* NOTE: remove this margin once the Instagram section is again enabled */

    & .faq {
      @apply mb-6;
    }
  }

  &.contact {
    @apply mb-32;

    & form {
      @apply mt-24;

      & .inputs {
        @apply flex flex-row space-x-4 mb-6;

        & > div {
          @apply flex-1;
        }
      }
    }
  }
}

@media only screen and (min-width: 981px) {
  .cover {
    & .mobile-only {
      @apply hidden;
    }
  }
}

@media only screen and (max-width: 980px) {
  .cover {
    height: 170vw;

    & .desktop-only {
      @apply hidden;
    }
  }

  section {
    @apply overflow-hidden;

    &.faqs {
      & .faq {
        @apply mx-6;
      }
    }

    &.contact {
      @apply mb-32;

      & form {
        @apply mx-6;

        & .inputs {
          @apply flex flex-col space-x-0 mb-0;

          & > div {
            @apply flex-1 mb-4;
          }
        }
      }
    }
  }
}
</style>
