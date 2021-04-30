<template>
  <header class="header">
    <div class="container header__container">
      <a href="https://lifehacker.ru/" class="header__logo header__logo--main">
        <svg>
          <use xlink:href="~/assets/icons.sprite.svg#logo-usage"></use>
        </svg>
      </a>
      <a href="https://cordiant.ru" class="header__logo header__logo--partner">
        <svg>
          <use xlink:href="~/assets/icons.sprite.svg#partnerLogo-usage"></use>
        </svg>
      </a>
    </div>
  </header>
</template>

<script>
export default {
  name: 'PageHeader',
}
</script>

<style scoped lang="scss">
.header {
  padding: 0.6875rem 0;
  position: relative;

  &::before {
    content: '';
    position: absolute;
    display: block;
    left: 0;
    right: 0;
    top: 0;
    height: 60px;
    background: linear-gradient(180deg, #000, rgba(0, 80, 138, 0));
    z-index: -1;

    @media (min-width: 768px) {
      height: 110px;
    }
  }

  &__container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 100%;
  }

  &__logo {
    svg {
      fill: #fff;
    }

    &--main {
      height: 14px;
      width: 75px;

      @media (min-width: 768px) {
        width: 99px;
        height: 18px;
      }
    }

    &--partner {
      width: 116px;
      height: 14px;

      @media (min-width: 768px) {
        width: 154px;
        height: 18px;
      }
    }
  }

  @media (min-width: 768px) {
    padding: 20px 0;
  }

  @media (min-width: 1024px) {
    padding: 16px 0;
  }
}
</style>
