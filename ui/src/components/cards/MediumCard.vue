<template>
  <div class="medium-card-wrapper">
    <router-link
      class="medium-card"
      :class="{ 'add-margins': addMargins }"
      tag="a"
      :to="link || ''"
    >
      <div
        class="medium-card_image"
        :style="background"
      />
      <div class="medium-card_content">
        <p class="medium-card_title hide-text">
          {{ title }}
        </p>
        <p class="medium-card_description hide-text">
          {{ description }}
        </p>
      </div>
    </router-link>
  </div>
</template>

<script>
import { FormatHelper } from '@/js/helpers/format'

export default {

  name: 'MediumCard',

  props: {
    title: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      default: ''
    },
    description: {
      type: String,
      default: ''
    },
    addMargins: {
      type: Boolean,
      default: false
    },
    link: {
      type: String,
      default: ''
    }
  },

  computed: {
    defaultImage () {
      return `${process.env.BASE_URL}images/default-recipe-image.png`
    },
    background () {
      return FormatHelper.backgroundImageStyle(this.image || this.defaultImage)
    }
  }

}
</script>

<style lang="scss">
@import '~@/assets/scss/variables';

.medium-card {
  display: block;
  width: 100%;
  border-radius: 4px;
  @include mdElevationElement('card');

  &.add-margins {
    margin: 16px;
  }

  .medium-card_image {
    width: 100%;
    padding-bottom: calc(100% / 16 * 9);
    border-radius: 4px 4px 0 0;
    @include background();
  }

  .medium-card_content {
    padding: 16px;

    p {
      margin: 0;
    }

    .medium-card_title {
      font-size: 20px;
      font-weight: 500;
      margin-bottom: 20px;
      max-height: 1.4em;
    }

    .medium-card_description {
      color: $secondary-text-color;
      font-size: 14.5px;
      max-height: calc(2 * 1.4em);
    }
  }
}
</style>
