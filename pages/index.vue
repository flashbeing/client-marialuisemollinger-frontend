<template>
  <main>
    <div class="cover">
      <!-- NOTE: add here video in case -->
    </div>
    <section class="main-features center compact">
      <FeatureBox
        img-name="marialuise"
        :title="$t('page.home.features.hello.title')"
        desc-translation-key="page.home.features.hello.desc"
        filled
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
      />
      <FaqItem
        v-for="faq in faqs"
        :key="faq.title"
        :title="faq.title"
        :content="faq.desc"
      ></FaqItem>
    </section>
    <section class="instagram center compact">
      <h2>Instagram</h2>
      <!-- TODO: add here reviews iFrame -->
    </section>
    <section class="contact center compact">
      <div>
        <SectionTitle
          :title="$t('page.home.contact.title')"
          :subtitle="$t('page.home.contact.subtitle')"
        />
      </div>
      <form>
        <div>
          <TextArea
            v-model="contactForm.message"
            :placeholder="$t('page.home.contact.message')"
            aspect="fill"
          />
        </div>
        <div>
          <Checkbox
            v-model="contactForm.terms"
            :label="$t('page.home.contact.iAcceptPrivacyPolicy')"
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
            <Button :value="$t('page.home.contact.send')" aspect="fill" />
          </div>
        </div>
      </form>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      contactForm: {},
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
  },

  methods: {
    getFaqItem(id) {
      return {
        title: this.$t('page.home.faq.faqs.' + id + '.title'),
        desc: this.$t('page.home.faq.faqs.' + id + '.desc'),
      }
    },
  },
}
</script>

<style lang="postcss" scoped>
h2 {
  @apply text-4xl text-primary text-center uppercase font-bold;
}

.cover {
  @apply bg-cover bg-center bg-no-repeat bg-placeholder;

  height: 70vh;
  min-height: 250px;
}

section {
  @apply my-10;

  & .instagram {
    & h2 {
      @apply mb-8;
    }
  }
}

@media only screen and (max-width: 980px) {
  .cover {
    height: 30vh;
  }
}
</style>
