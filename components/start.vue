<template>
  <div class="start">
    <layout relative>
      <div
        slot="left"
        v-lazy:background-image="'start.png'"
        class="start__left"
      />
      <div class="start__right">
        <div class="start__content">
          <div class="start__title">
            <span
              >Узнаете&amp;nbsp;ли вы&amp;nbsp;Россию по&amp;nbsp;дорогам?</span
            >
            <div class="start__container container">
              <svg class="start__title-recognize">
                <use
                  xlink:href="~/assets/icons.sprite.svg#recognize-usage"
                ></use></svg
              ><svg class="start__title-by-roads">
                <use
                  xlink:href="~/assets/icons.sprite.svg#by_roads-usage"
                ></use>
              </svg>
            </div>
          </div>
          <div class="start__container container">
            <p class="start__description">
              Мы&nbsp;составили этот тест вместе с&nbsp;производителем шин
              <a class="link" href="https://cordiant.ru">Cordiant</a>, чтобы
              вы&nbsp;проверили, сможете&nbsp;ли отличить российские дороги
              от&nbsp;остальных. Активируйте внутреннего Шерлока&nbsp;—
              и&nbsp;вперёд! Пройдёте тест до&nbsp;конца&nbsp;— получите
              скидку&nbsp;15% на&nbsp;зимнюю резину.
            </p>
            <div class="start__buttons">
              <button class="button" @click="$emit('start')">
                Пройти тест!
              </button>
            </div>
          </div>
        </div>
      </div>
      <page-footer>
        <social class="social--footer" />
      </page-footer>
    </layout>
  </div>
</template>

<script>
import layout from '~/components/layout'
import pageFooter from '~/components/footer'
import social from '~/components/social'
export default {
  name: 'StartScreen',
  components: {
    layout,
    pageFooter,
    social,
  },
}
</script>

<style scoped lang="scss">
.start {
  display: flex;
  flex: 1 0 auto;
  flex-direction: column;

  &__container {
    @media (min-width: 768px) {
      width: 428px;
      margin: 0 auto;
    }
  }

  &__content {
    border-top: 2px solid #fff;
    border-bottom: 2px solid #fff;
    padding: 24px 0 70px;
    background-color: #004373;

    @media (min-width: 768px) {
      padding: 24px 0 84px;
      width: 632px;
      margin: 140px auto 0;
      border-left: 2px solid #fff;
      border-right: 2px solid #fff;
    }

    @media (min-width: 1024px) {
      margin-right: 0;
      margin-top: 72px;
      border-right: none;
    }
  }

  &__left {
    flex: 1 0 auto;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 0;
  }

  &__title {
    font-family: Play, sans-serif;
    font-size: 20px;
    padding-bottom: 24px;
    margin-bottom: 32px;
    position: relative;
    text-indent: -9999px;
    display: flex;
    flex-direction: column;

    span {
      display: block;
      height: 0;
      overflow: hidden;
    }

    &::after,
    &::before {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      display: block;
      width: 100%;
      border-top: 2px solid #fff;
    }

    &::after {
      bottom: -8px;
    }
  }

  &__title-recognize {
    height: 29px;

    @media (min-width: 440px) {
      margin-bottom: 14px;
    }
  }

  &__title-by-roads {
    height: 51px;
  }

  &__subtitle {
    font-size: 40px;
    display: block;
    text-transform: uppercase;
    white-space: nowrap;
  }

  &__description {
    margin-bottom: 40px;
  }

  &__buttons {
    display: flex;
    justify-content: center;

    @media (min-width: 768px) {
      justify-content: flex-start;
    }
  }
}

.social--footer {
  display: flex;
  justify-content: center;
  margin-bottom: 40px;
}
</style>
