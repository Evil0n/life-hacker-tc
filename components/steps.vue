<template>
  <div class="steps">
    <layout v-if="question">
      <div slot="left" class="steps__left">
        <div class="steps__left-panel"></div>
        <div class="steps__left-mirror" :class="resultClass"></div>

        <div
          v-lazy:background-image="question.image"
          class="start__left steps__left-image"
        />
      </div>
      <div class="steps__content content">
        <div class="steps__container container">
          <div class="steps__counter">{{ question.id }}/6</div>
          <div class="steps-question">
            <div class="steps-question__title">Где эта дорога?</div>
            <transition name="fade" mode="out-in">
              <div v-if="feedback" key="answer" class="steps-answer">
                <div class="steps-answer__feedback" v-html="feedback" />
                <div
                  v-if="question.promo"
                  class="steps-answer__promo"
                  v-html="question.promo"
                />
                <div class="steps-answer__buttons">
                  <button class="button" @click="sendAnswer">Далее</button>
                </div>
              </div>
              <div v-else key="question" class="steps-question__variants">
                <div
                  v-for="variant in question.answers"
                  :key="variant.id"
                  class="steps-question__variants-item"
                >
                  <input
                    :id="variant.id"
                    type="radio"
                    @change="setAnswer(variant)"
                  />
                  <label :for="variant.id">
                    <span v-html="variant.text" />
                  </label>
                </div>
              </div>
            </transition>
          </div>
        </div>
      </div>
      <page-footer>
        <div />
      </page-footer>
    </layout>
  </div>
</template>

<script>
import layout from '~/components/layout'
import pageFooter from '~/components/footer'

export default {
  components: {
    layout,
    pageFooter,
  },
  props: {
    question: {
      type: Object,
      default: () => ({}),
    },
  },
  data() {
    return {
      answer: undefined,
    }
  },
  computed: {
    feedback() {
      if (this.answer) {
        return this.answer.feedback
      }
      return undefined
    },
    resultClass() {
      if (this.answer) {
        return {
          'steps__left-mirror--success': this.answer.isRight,
          'steps__left-mirror--error': !this.answer.isRight,
        }
      }
      return {}
    },
  },
  methods: {
    setAnswer(variant) {
      this.$set(this, 'answer', variant)
    },
    sendAnswer() {
      this.$emit('answer', { ...this.answer })
      this.$set(this, 'answer', undefined)
    },
  },
}
</script>

<style scoped lang="scss">
.steps-question {
  &__title {
    font-size: 37px;
    line-height: 43px;
    font-family: Play, sans-serif;
    margin-bottom: 32px;
    font-weight: 700;
    text-align: center;

    @media (min-width: 440px) {
      font-size: 45px;
      line-height: 52px;
    }
  }

  &__variants {
    margin-bottom: 40px;

    label {
      display: flex;
      align-items: center;
      min-height: 82px;
      position: relative;
      cursor: pointer;
      padding: 18px 16px;
      border-radius: 3px;
      background: hsla(0, 0%, 100%, 0.2);
      transition: 0.3s;
      color: #fff;

      &:hover {
        background: #7dbfff;
        color: #004373;
      }

      @media (min-width: 768px) {
        padding: 16px 48px;
      }
    }

    input {
      display: none;

      &:checked + label {
        background: #fff;
        color: #004373;
      }
    }

    &--disabled {
      pointer-events: none;
    }
  }

  &__variants-item {
    margin-bottom: 16px;
  }
}

.steps-answer {
  &__feedback {
    font-size: 18px;
    line-height: 26px;
    font-weight: 700;
    margin-bottom: 24px;
  }

  &__promo {
    margin-bottom: 40px;
  }

  &__buttons {
    display: flex;
    justify-content: center;

    @media (min-width: 768px) {
      justify-content: flex-start;
    }
  }

  @media (min-width: 768px) {
    width: 370px;
    margin: 0 auto;
  }

  @media (min-width: 1280px) {
    width: 100%;
    margin-top: 16px;
    margin-left: 0;
  }
}

.steps {
  display: flex;
  flex-direction: column;
  flex: 1 0 auto;

  &__container {
    padding: 0;

    @media (min-width: 768px) {
      width: 456px;
      margin: 0 auto;
    }

    @media (min-width: 1280px) {
      width: 90%;
      min-height: 450px;
    }
  }

  &__left {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    flex: 1 0 auto;
    position: relative;
  }

  &__left-panel {
    left: 0;
    width: 100%;
    height: 100%;
    background-size: contain;
    background-position: 0 100%;
    background-image: url(~/assets/car.png);
  }

  &__left-mirror,
  &__left-panel {
    position: absolute;
    top: 0;
    background-repeat: no-repeat;
    z-index: 1;
  }

  &__left-mirror {
    width: 128px;
    height: 58px;
    left: 50%;
    transform: translateX(-50%);
    background-image: url(~/assets/mirror.sprite.png);
    background-size: 384px auto;

    &--success {
      background-position: -256px 0;

      @media (min-width: 440px) {
        background-position: -352px 0;
      }

      @media (min-width: 768px) {
        background-position: -516px 0;
      }

      @media (min-width: 1024px) {
        background-position: -688px 0;
      }

      @media (min-width: 1280px) {
        background-position: -640px 0;
      }
    }

    &--error {
      background-position: -128px 0;

      @media (min-width: 440px) {
        background-position: -176px 0;
      }

      @media (min-width: 768px) {
        background-position: -258px 0;
      }

      @media (min-width: 1024px) {
        background-position: -344px 0;
      }

      @media (min-width: 1280px) {
        background-position: -320px 0;
      }
    }

    @media (min-width: 440px) {
      width: 176px;
      height: 81px;
      background-size: 528px auto;
    }

    @media (min-width: 768px) {
      width: 258px;
      height: 119px;
      background-size: 774px auto;
    }

    @media (min-width: 1024px) {
      width: 344px;
      height: 158px;
      background-size: 1032px auto;
    }

    @media (min-width: 1280px) {
      width: 320px;
      height: 148px;
      background-size: 960px auto;
      left: inherit;
      transform: translateX(0);
      right: 48px;
    }
  }

  &__left-image {
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 50%;
    flex: 1 0 auto;

    @media (min-width: 768px) {
      background-position: bottom;
    }
  }

  &__counter {
    margin-bottom: 16px;
  }

  &__content {
    @media (min-width: 440px) {
      padding-top: 16px;
    }

    @media (min-width: 1280px) {
      border-top: none;
      flex: 1 0 auto;
      border-left: 2px solid #fff;
      padding-top: 0;
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      align-items: center;
      font-size: 18px;
      line-height: 26px;
    }
  }
}
</style>
