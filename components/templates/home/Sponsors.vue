<template>
  <div
    class="transition-colors duration-300 ease-linear bg-light-elevatedSurface dark:bg-dark-elevatedSurface shadow-nuxt"
  >
    <div class="container px-4 py-12 mx-auto text-centshadow-nuxter">
      <section class="px-4">
        <h1 class="mb-2 text-3xl font-medium uppercase sm:mb-0">
          {{ $t('homepage.sponsors.title') }}
        </h1>
        <SponsoringIllustration
          id="sponsor-img"
          class="inline-block float-right lg:ml-4"
        />
        <div
          class="pt-6 pb-12 leading-loose text-left transition-colors duration-300 ease-linear text-light-onSurfaceSecondary dark:text-dark-onSurfaceSecondary"
        >
          <p>
            {{ $t('homepage.sponsors.description') }}
          </p>
        </div>
        <div
          v-for="(group, groupKey) in sponsors"
          :key="groupKey"
          class="pb-8 text-center"
        >
          <h2
            class="pb-8 font-medium uppercase transition-colors duration-300 ease-linear text text-light-onSurfacePrimary dark:text-dark-onSurfacePrimary"
          >
            <span class="pb-2 border-b-2 border-nuxt-lightgreen">
              {{ groupKey }}
            </span>
          </h2>
          <a
            v-for="(sponsor, i) in group"
            :key="i"
            class="inline-block m-4 sponsor"
            :href="`${sponsor.url}?ref=nuxt`"
            target="_blank"
            rel="noopener sponsored"
          >
            <ClientOnly>
              <img
                :src="`/img/sponsors/${$colorMode.value}/${sponsor.img}`"
                :alt="sponsor.name"
                class="inline-block"
                :class="sponsor.class"
                loading="lazy"
              />
            </ClientOnly>
          </a>
        </div>
        <div class="pb-8 text-center">
          <h2
            class="pb-8 font-medium uppercase transition-colors duration-300 ease-linear text text-light-onSurfacePrimary dark:text-dark-onSurfacePrimary"
          >
            <span class="pb-2 border-b-2 border-nuxt-lightgreen">
              Educational Partner
            </span>
          </h2>
          <a
            class="inline-block m-4 sponsor"
            href="https://vueschool.io?friend=nuxt"
            target="_blank"
            rel="noopener sponsored"
          >
            <ClientOnly>
              <img
                :src="`/img/partners/${$colorMode.value}/vueschool.svg`"
                alt="Vue School logo"
                title="Vue School is an official Nuxt.js Educational Partner"
                class="inline-block h-10"
                loading="lazy"
              />
            </ClientOnly>
          </a>
        </div>
        <div class="text-center">
          <AppButton
            :to="localePath({ name: 'sponsor-nuxtjs' })"
            data-cy="sponsors"
            class="px-6 py-3 text-base"
          >
            <GithubIcon slot="icon" class="inline-block h-5 mr-1 -mt-1" />
            {{ $t('homepage.sponsors.become_a_sponsor') }}
          </AppButton>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import GithubIcon from '~/assets/icons/github.svg?inline'
import SponsoringIllustration from '~/assets/illustrations/sponsoring.svg?inline'

export default {
  components: {
    GithubIcon,
    SponsoringIllustration
  },
  data() {
    return {
      sponsors: {
        partners: [
          {
            name: 'Strapi',
            url: 'https://strapi.io/',
            img: 'strapi-logo.svg',
            class: 'h-12'
          },
          {
            name: 'Ship Shape',
            url: 'https://shipshape.io/',
            img: 'shipshape-logo.svg',
            class: 'h-12'
          }
        ],
        gold: [
          {
            name: 'VueMastery',
            img: 'vueMastery-brand.svg',
            url: 'https://www.vuemastery.com/',
            class: 'h-10'
          },
          {
            name: 'Legal Nature',
            img: 'legalnature-logo.svg',
            url: 'https://www.legalnature.com/',
            class: 'h-10'
          }
        ],
        special: [
          {
            name: 'Google Chrome',
            img: 'google-chrome.svg',
            url: 'https://www.google.com/chrome/',
            class: 'h-12'
          }
        ]
      }
    }
  }
}
</script>

<style lang="scss">
.sponsor {
  & img {
    filter: grayscale(100%);
    opacity: 0.75;
    transition: all 0.5s;
  }

  &:hover {
    & img {
      filter: grayscale(0%);
      opacity: 1;
    }
  }
}

#sponsor-img {
  shape-outside: circle(49.5% at 90px 95px);
}
</style>
