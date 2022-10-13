<template>
    <section class="popup" v-if="isOpened">
        <div class="popup__area" @click="closePopup"></div>
        <div class="popup__container container">
            <button class="popup__button button button--close" @click="closePopup"></button>
            <LogoComponent class="popup__logo" :color="'#55B03B'"/>
            <template>
                <product-popup
                    v-if="isProductPopup"
                    :dataPopup="dataPopup"
                />
                <quiz-start
                    v-if="isQuizPopup && isQuizStart"
                    @to-next-step="toNextStep('isQuizStep1')"
                />
                <quiz-step-1
                    v-if="isQuizStep1"
                    @to-next-step="toNextStep('isQuizStep2')"
                    @back="toNextStep('isQuizStart')"
                />
                <quiz-step-2
                    v-if="isQuizStep2"
                    @to-next-step="toNextStep('isQuizStep3')"
                    @back="toNextStep('isQuizStep1')"
                />
                <quiz-step-3
                    v-if="isQuizStep3"
                    @to-next-step="toNextStep('isQuizFinish')"
                    @back="toNextStep('isQuizStep2')"
                />
                <quiz-finish
                    v-if="isQuizFinish"
                    @closePopup="closePopup"
                    @back="toNextStep('isQuizStep3')"
                />
            </template>
        </div>
    </section>
</template>

<script>
import LogoComponent from '../ui/LogoComponent.vue'
import ProductPopup from '../blocks/ProductPopup.vue'
import QuizStart from '../blocks/quiz/QuizStart.vue'
import QuizStep1 from '../blocks/quiz/QuizStep1.vue'
import QuizStep2 from '../blocks/quiz/QuizStep2.vue'
import QuizStep3 from '../blocks/quiz/QuizStep3.vue'
import QuizFinish from '../blocks/quiz/QuizFinish.vue'

export default {
  props: ['isOpened', 'dataPopup', 'isProductPopup', 'isQuizPopup'],
  components: {
    LogoComponent,
    ProductPopup,
    QuizStart,
    QuizStep1,
    QuizStep2,
    QuizStep3,
    QuizFinish
  },
  data () {
    return {
      isQuizStart: true,
      isQuizStep1: false,
      isQuizStep2: false,
      isQuizStep3: false,
      isQuizFinish: false
    }
  },
  methods: {
    resetSteps () {
      this.isQuizStart = false
      this.isQuizStep1 = false
      this.isQuizStep2 = false
      this.isQuizStep3 = false
      this.isQuizFinish = false
    },
    closePopup () {
      this.resetSteps()
      this.$emit('togglePopup')
      this.isQuizStart = true
    },
    toNextStep (activeStep) {
      this.resetSteps()
      switch (activeStep) {
        case 'isQuizStart':
          this.isQuizStart = true
          break
        case 'isQuizStep1':
          this.isQuizStep1 = true
          break
        case 'isQuizStep2':
          this.isQuizStep2 = true
          break
        case 'isQuizStep3':
          this.isQuizStep3 = true
          break
        case 'isQuizFinish':
          this.isQuizFinish = true
          break
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 102;
  background-color: rgba(180, 180, 180, .4);
  &__area {
      position: absolute;
      width: 100vw;
      height: 100vh;
      backdrop-filter: blur(5px);
      z-index: 0;
      cursor: pointer;
  }
  &__container {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: $baseColor;
      padding: 32px 20px;
      overflow-y:scroll;
  }
  &__logo {
    display: none;
  }
  @media (min-width: $tablet-min) {
      &__container {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: $baseColor;
        max-width: 1200px;
        height: 570px;
        border-radius: 70px;
        padding: 50px;
        overflow-y: visible;
    }
    &__logo {
        position: absolute;
        display: block;
        right: 50px;
        z-index: 10;
        max-width: 100px;
    }
  }
  @media (min-width: $desktop) {
      &__container {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: $baseColor;
        max-width: 1200px;
        height: 570px;
        border-radius: 70px;
        padding: 50px;
    }
    &__logo {
        position: absolute;
        right: 50px;
        z-index: 10;
    }
  }
}

template {
    display: block;
}
.button {
    &--close {
        position: absolute;
        right: 12px;
        top: 12px;
        width: 20px;
        height: 20px;
        border: 2px solid $mainColor;
        border-radius: 50%;
        z-index: 100;
        &::before,
        &::after {
            content: "";
            position: absolute;
            top: 2px;
            right: 7px;
            height: 12px;
            width: 2px;
            background-color: $mainColor;
            border-radius: 5px;
        }
        &::before {
            transform: rotate(45deg);
        }
        &::after {
            transform: rotate(-45deg);
        }
      @media (min-width: $tablet-min) {
        right: 0;
        top: 0;
        border: 2px solid $baseColor;
        &::before,
        &::after {
            background-color: $baseColor;
        }
      }
    }
}
</style>
