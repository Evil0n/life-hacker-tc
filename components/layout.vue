<template>
  <div
    class="layout"
    :class="{ 'layout--relative': relative, 'layout--fixed': !relative }"
  >
    <div class="layout__content">
      <div class="layout__content-side layout__content-side--left">
        <slot name="left" />
      </div>
      <div class="layout__content-side layout__content-side--right">
        <slot />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Layout',
  props: {
    relative: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style scoped lang="scss">
.layout {
  display: flex;
  flex-direction: column;
  flex: 1 0 auto;
  position: relative;

  &__content-side--left {
    min-height: 15.625rem;
    position: relative;
    overflow: hidden;

    @media (min-width: 1280px) {
      min-height: auto;
    }
  }

  &--fixed {
    .layout__content-side--left {
      height: 268px;
      min-height: auto;
      flex: 0 0 auto;

      @media (min-width: 440px) {
        height: 268px;
      }
      @media (min-width: 768px) {
        height: 466px;
      }
      @media (min-width: 1024px) {
        height: 623px;
      }
      @media (min-width: 1280px) {
        height: auto;
      }
    }
  }

  &__content-side,
  &__content {
    display: flex;
    flex-direction: column;
    flex: 1 0 auto;
  }

  &__content {
    position: relative;

    @media (min-width: 1280px) {
      flex-direction: row;
    }
  }

  &__content-side {
    &--right {
      @media (min-width: 1920px) {
        position: relative;
        z-index: 100;
      }
    }

    @media (min-width: 1280px) {
      width: 50%;
      flex: 1 0;
    }
  }

  &--relative {
    @media (min-width: 768px) {
      .layout__content-side--left {
        position: absolute;
        left: 0;
        top: 0;
        bottom: 0;
        z-index: 1;
        width: 100%;
      }

      .layout__content-side--right {
        position: relative;
        z-index: 2;
      }
    }
  }
}
</style>
