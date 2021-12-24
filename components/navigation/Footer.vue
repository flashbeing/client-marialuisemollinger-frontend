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
              <a href="mailto:info@marylukocht.it">info@marylukocht.it</a>
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
          <a
            href="https://www.iubenda.com/privacy-policy/48275665"
            class="iubenda-white iubenda-noiframe iubenda-embed iubenda-noiframe"
            title="Datenschutzerklärung "
            >Datenschutzerklärung</a
          >
          <script type="text/javascript">
            ;(function (w, d) {
              var loader = function () {
                var s = d.createElement('script'),
                  tag = d.getElementsByTagName('script')[0]
                s.src = 'https://cdn.iubenda.com/iubenda.js'
                tag.parentNode.insertBefore(s, tag)
              }
              if (w.addEventListener) {
                w.addEventListener('load', loader, false)
              } else if (w.attachEvent) {
                w.attachEvent('onload', loader)
              } else {
                w.onload = loader
              }
            })(window, document)
          </script>
        </div>
        <div class="col">
          <div class="socials">
            <a href="https://www.instagram.com/marylukocht/" target="_blank"
              ><div class="social clickable instagram">
                <Icon name="instagram" /></div
            ></a>
            <a
              href="https://www.facebook.com/people/Marylu-kocht/100068188207265/"
              target="_blank"
              ><div class="social clickable facebook">
                <Icon name="facebook" /></div
            ></a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<style lang="postcss" scoped>
footer {
  @apply bg-primary py-10 font-light;

  & .cols {
    @apply flex flex-row;

    & .col {
      @apply text-white text-base flex-1;

      & .logo {
        width: 150px;
      }

      & .copy {
        @apply text-xs mt-4;
      }

      & li {
        @apply mb-2 text-sm;
      }

      & .socials {
        @apply flex flex-row flex-row-reverse;

        & .social {
          @apply mr-3 border border-white rounded-md flex items-center justify-center;

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
}

@media only screen and (max-width: 980px) {
  footer {
    @apply text-center;

    & .cols {
      @apply flex-col;

      & .col {
        @apply mb-6;

        & .socials {
          @apply justify-center;
        }
      }
    }
  }
}
</style>
