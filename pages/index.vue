<template>
  <div class="main">
    <page-header class="main__header" />
    <transition name="fade" mode="out-in" class="main__content">
      <start v-if="stage === 'start'" key="start" @start="startTest" />
      <steps
        v-if="stage === 'steps'"
        key="steps"
        :question="currentQuestion"
        @answer="setAnswer"
      />
      <finish
        v-if="stage === 'finish'"
        key="finish"
        :count-right-answers="countRightAnswers"
        @restart="restart"
      />
    </transition>
  </div>
</template>

<script>
import PageHeader from '~/components/header'
import start from '~/components/start'
import steps from '~/components/steps'
import finish from '~/components/finish'
import { questions } from '~/assets/questions'

export default {
  name: 'Stepper',
  components: { PageHeader, start, steps, finish },
  data() {
    return {
      stage: 'start',
      answers: [],
    }
  },
  computed: {
    currentQuestion() {
      return questions[this.answers.length]
    },
    countRightAnswers() {
      return this.answers.filter((answer) => answer.isRight).length
    },
  },
  methods: {
    startTest() {
      this.stage = 'steps'
      this.$set(this, 'answers', [])
    },
    setAnswer(answer) {
      this.answers.push(answer)
      if (this.answers.length === questions.length) {
        this.stage = 'finish'
      }
    },
    restart() {
      this.stage = 'steps'
      this.$set(this, 'answers', [])
    },
  },
}
</script>

<style scoped lang="scss">
.main {
  position: relative;
  display: flex;
  flex-direction: column;
  flex: 1 0 auto;

  &__header {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    z-index: 999;
  }

  &__content {
    display: flex;
    flex-direction: column;
    flex: 1 0 auto;
  }
}
</style>
