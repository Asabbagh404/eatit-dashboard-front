<template>
  <div class="row row-equal">
    <div class="flex xs12 md12 xl8">
      <va-card stripe stripe-color="info">
        <va-card-title>
          {{ $t('dashboard.info.previewing') }}
        </va-card-title>
        <va-card-content>
          <va-image
            :src="images[0]"
            style="height: 200px;"
          />
          <div class="mt-3">
            <va-button color="primary" target="_blank" href="https://github.com/epicmaxco/vuestic-ui">
              {{$t('dashboard.info.visitWebsite')}}
            </va-button>
          </div>
        </va-card-content>
      </va-card>
    </div>
  </div>
</template>

<script>
import { useGlobalConfig } from 'vuestic-ui'

export default {
  name: 'DashboardInfoBlock',
  data () {
    return {
      infoTiles: [{
        color: 'success',
        value: '803',
        text: 'commits',
        icon: '',
      }, {
        color: 'danger',
        value: '57',
        text: 'components',
        icon: '',
      }, {
        color: 'info',
        value: '5',
        text: 'teamMembers',
        icon: '',
      }],
      modal: false,
      currentImageIndex: 0,
      images: [
        'https://i.imgur.com/qSykGko.jpg',
        'https://i.imgur.com/jYwT08D.png',
        'https://i.imgur.com/9930myH.jpg',
        'https://i.imgur.com/2JxhWD6.jpg',
        'https://i.imgur.com/MpiOWbM.jpg',
      ],
    }
  },
  methods: {
    showModal () {
      this.modal = true
    },
    showPrevImage () {
      this.currentImageIndex = !this.currentImageIndex ? this.images.length - 1 : this.currentImageIndex - 1
    },
    showNextImage () {
      this.currentImageIndex = this.currentImageIndex === this.images.length - 1 ? 0 : this.currentImageIndex + 1
    },
  },
  computed: {
    theme() {
      return useGlobalConfig().getGlobalConfig().colors || {}
    }
  }
}
</script>

<style lang="scss" scoped>
  .row-separated {
    .flex + .flex {
      border-left: 1px solid var(--va-background);
    }

    // @include media-breakpoint-down(xs) {
    //   p:not(.display-2) {
    //     font-size: 0.875rem;
    //   }
    // }
  }

  .rich-theme-card-text {
    line-height: 24px;
  }

  .dashboard {
    .va-card__header--over {
      // @include media-breakpoint-up(md) {
      //   padding-top: 0 !important;
      // }
    }

    .va-card__image {
      // @include media-breakpoint-up(md) {
      //   padding-bottom: 0 !important;
      // }
    }
    // .image-card {
    //   position: relative;
    //   .va-button {
    //     position: absolute;
    //   }
    // }
  }
</style>
