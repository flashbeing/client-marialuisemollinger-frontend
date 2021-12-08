<template>
  <footer>
    <div class="center">
      <div class="cols">
        <div class="col">
          <Icon name="logo" class="logo" />
          <p class="copy">© Marylu kocht</p>
        </div>
        <div class="col">
          <ul>
            <li>Marialuise Möllinger</li>
            <li><a href="tel:+393405947912">+39 340 594 7912</a></li>
            <li>
              <a href="mailto:info@marvlukocht.it">info@marvlukocht.it</a>
            </li>
          </ul>
        </div>
        <div class="col">
          <ul>
            <li>{{ $t('footer.street') }}</li>
            <li>{{ $t('footer.town') }}</li>
            <li>{{ $t('footer.state') }}</li>
          </ul>
        </div>
        <div class="col">
          <ul>
            <li>{{ $t('footer.sdi') }}: T9K4ZHO</li>
            <li>{{ $t('footer.vat') }}: 03092920218</li>
          </ul>
        </div>
        <div class="col">
          <div class="socials">
            <a
              href="https://www.facebook.com/people/Marylu-kocht/100068188207265/"
              target="_blank"
              ><div class="social clickable facebook">
                <Icon name="facebook" /></div
            ></a>
            <a href="https://www.instagram.com/marylukocht/" target="_blank"
              ><div class="social clickable instagram">
                <Icon name="instagram" /></div
            ></a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<style lang="postcss" scoped>
footer {
  @apply bg-primary py-10;

  & .cols {
    @apply flex flex-row;

    & .col {
      @apply text-white text-base flex-1;

      & li {
        @apply mb-2;
      }
    }

    & .socials {
      & .social {
        @apply inline-block mr-2 border border-white rounded-md flex items-center justify-center;

        width: 40px;
        height: 40px;

        & svg {
          height: 20px;
          fill: theme(colors.white);
        }
      }
    }
  }
}
</style>
