<template>
  <div class="finish">
    <layout>
      <div slot="left" class="finish__left">
        <div
          v-lazy:background-image="result.image"
          class="finish__image-left"
        />
      </div>
      <div class="finish__right">
        <div class="finish__result">
          <div class="finish__content content">
            <div class="finish__container container">
              <div class="finish__title" v-html="result.title"></div>
              <div
                class="finish__description"
                v-html="result.description"
              ></div>
              <div class="finish__actions">
                <div class="finish__repeat">
                  <button
                    class="button button--image"
                    @click="$emit('restart')"
                  >
                    <svg class="button__image">
                      <use
                        xlink:href="~/assets/icons.sprite.svg#repeat-usage"
                      ></use></svg
                    >Пройти ещё раз
                  </button>
                </div>
                <social class="finish__social" />
              </div>
            </div>
          </div>
          <div class="finish__content content">
            <div class="finish__container container">
              <div class="finish__product">
                <div class="finish__product-text">
                  <span class="bold"
                    >Чтобы любая дорога была для вас безопасной</span
                  >, следите за&nbsp;качеством резины и&nbsp;переобувайтесь
                  вовремя. С&nbsp;зимними шинами Cordiant ваша машина будет
                  уверенно выезжать из&nbsp;снежных заносов и&nbsp;стабильно
                  вести себя на&nbsp;обледенелых трассах. Прямо сейчас комплект
                  зимних шин Cordiant можно купить
                  <span class="bold">со&nbsp;скидкой 15%</span>! Просто оформите
                  заказ на&nbsp;<a class="link" href="https://koleso.ru"
                    >koleso.ru</a
                  >, введите промокод
                  <span class="promo light-green">CORDIHACKER</span>
                  в&nbsp;комментариях. Оператор перезвонит вам для расчёта
                  скидки и&nbsp;подтверждения заказа. Промокод действует
                  до&nbsp;<span class="bold light-green">XX.XX.2020</span>
                  при заказе следующих моделей: Cordiant Snow Cross, Cordiant
                  Snow Cross&nbsp;2, Cordiant Winter Drive, Cordiant Winter
                  Drive&nbsp;2, Cordiant Polar&nbsp;SL, дюймы
                  с&nbsp;15&nbsp;по&nbsp;18.
                </div>
                <div class="finish__product-buttons">
                  <a href="https://koleso.ru" class="button button--product">
                    Купить шины со скидкой
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
        <page-footer class="footer--finish">
          <team class="finish__team" />
        </page-footer>
      </div>
    </layout>
  </div>
</template>

<script>
import layout from '~/components/layout'
import pageFooter from '~/components/footer'
import { results } from '~/assets/results'

export default {
  name: 'Finish',
  components: {
    layout,
    pageFooter,
  },
  props: {
    countRightAnswers: {
      type: Number,
      required: true,
    },
  },
  computed: {
    result() {
      if (this.countRightAnswers > 4) {
        return results[2]
      }
      if (this.countRightAnswers > 2) {
        return results[1]
      }
      return results[0]
    },
  },
}
</script>

<style scoped lang="scss">
.finish {
  display: flex;
  flex: 1 0 auto;
  flex-direction: column;

  &__container {
    padding: 0;

    @media (min-width: 768px) {
      width: 428px;
      margin: 0 auto;
    }
  }

  &__content {
    @media (min-width: 1280px) {
      width: 100%;

      &:first-child {
        border-top: none;
      }
    }
  }

  &__result,
  &__right {
    @media (min-width: 1280px) {
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      flex-direction: column;
    }
  }

  &__left,
  &__right {
    flex: 1 0 auto;
    display: flex;
    flex-direction: column;
  }

  &__result {
    @media (min-width: 1280px) {
      width: 100%;
      flex: 1 0 auto;
      justify-content: center;
    }
  }

  &__right {
    @media (min-width: 1280px) {
      align-items: center;
      justify-content: flex-start;
      flex: 1 0 auto;
      border-left: 2px solid #fff;
      max-height: 100vh;
      overflow-y: auto;
      padding-top: 30px;
    }
  }

  &__image-left {
    flex: 1 0 auto;
    background-position: 0 100%;
    background-size: cover;
    background-repeat: no-repeat;

    @media (min-width: 1280px) {
      background-size: cover;
    }
  }

  &__title {
    margin-top: 14px;
    font-family: Play, sans-serif;
    font-size: 35px;
    line-height: 40px;
    margin-bottom: 16px;
    font-weight: 700;
  }

  &__description {
    font-family: Open Sans, sans-serif;
    font-size: 18px;
    line-height: 26px;
    font-weight: 700;
    margin-bottom: 40px;
  }

  &__actions,
  &__repeat,
  &__social {
    display: flex;
    justify-content: center;
  }

  &__actions {
    flex-direction: column;

    @media (min-width: 440px) {
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
    }
  }

  &__repeat {
    order: 1;
    margin-top: 24px;

    @media (min-width: 440px) {
      margin-top: 0;
      order: -1;
    }
  }

  &__product-text {
    margin-bottom: 40px;
  }

  &__product-buttons {
    display: flex;
    justify-content: center;

    @media (min-width: 1280px) {
      justify-content: flex-start;
    }
  }

  &__spacer {
    display: none;
    flex: 2;

    @media (min-width: 1280px) {
      display: block;
    }
  }

  &__team {
    margin-bottom: 40px;

    @media (min-width: 768px) {
      margin-bottom: auto;
    }
  }
}
.footer--finish {
  position: static;
  width: 100%;

  @media (min-width: 768px) {
    width: 428px;
    margin: 0 auto;

    /deep/ {
      .footer__container {
        width: 100%;
      }
    }
  }
}
</style>
