<template>
    <header class="header" v-on="handleScroll" :class="{scroll: isScroll}">
        <div class="header__container container">
            <a class="header__logo">
                <logo-component
                  :color="'#ffffff'"
                />
            </a>
            <ul class="header__menu menu menu--desktop">
                <li><a href="#benefits">Преимущества</a></li>
                <li><a href="#products">Продукция</a></li>
                <li><a href="#banner-form">Приобрети</a></li>
                <li><a href="#problems">Частые проблемы</a></li>
                <li><a href="#banner-instruction">Подобрать средство</a></li>
            </ul>
            <div class="header__burger" @click="menuOpened = !menuOpened" :class="{opened: menuOpened}">
            </div>
            <div class="header__social">
                <a class="vk" href="#">
                </a>
                <a class="youtube" href="#">
                </a>
            </div>
        </div>
        <transition name="fade">
            <div v-if="menuOpened" class="header__menu menu menu--mobile" :class="{opened: menuOpened}">
                <ul class="menu__list">
                    <li><a href="">Преимущества</a></li>
                    <li><a href="">Продукция</a></li>
                    <li><a href="">Приобрети</a></li>
                    <li><a href="">Частые проблемы</a></li>
                    <li><a href="">Подобрать средство</a></li>
                </ul>
            </div>
        </transition>
    </header>
</template>

<script>
import LogoComponent from './ui/LogoComponent.vue'
export default {
  components: {
    LogoComponent
  },
  data () {
    return {
      isScroll: false,
      limitPosition: 80,
      lastPosition: 0,
      menuOpened: false
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll () {
      if (this.lastPosition < window.scrollY && this.limitPosition < window.scrollY) {
        this.isScroll = true
      }
      if (this.lastPosition > window.scrollY && this.limitPosition > window.scrollY) {
        this.isScroll = false
      }
      this.lastPosition = window.scrollY
    }
  }
}
</script>

<style lang="scss" scoped>

.header {
    position: fixed;
    left: 0;
    right: 0;
    background-color: $mainColor;
    transition: all .5s;
    height: 48px;
    color: $baseColor;
    font-family: $mainFont;
    font-weight: 400;
    font-size: 17px;
    line-height: 26px;
    text-align: right;
    z-index: 101;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    &__container {
        display: flex;
        flex-direction: row-reverse;
        align-items: center;
        justify-content: space-between;
        z-index: 10;
    }
    &__burger {
        width: 24px;
        height: 2px;
        background-color: $baseColor;
        display: block;
        position: relative;
        transition: all .5s ease;
        &::before,
        &::after {
            content: '';
            width: 24px;
            height: 2px;
            background-color: $baseColor;
            display: block;
            position: absolute;
            transition: all .5s ease;
        }
        &::before {
            top: -6px;
        }
        &::after {
            bottom: -6px;
        }
        &.opened {
            background-color: transparent;
            &::before {
                top: 0;
                transform: rotate(45deg);
            }
            &::after {
                top: 0;
                transform: rotate(-45deg);
            }
        }
    }
    &__logo {
        position: absolute;
        top: 0px;
        left: 50%;
        transform: translateX(-50%);
        padding: 0 10px;
        height: 68px;
        &::after {
            transition: all .5s;
            content: '';
            background-color: $mainColor;
            position: absolute;
            height: 68px;
            width: 120px;
            border-radius: 0 0 11.1px 11.1px;
            left: 0;
            top: 0;
            z-index: -1;
        }
        & svg {
            max-width: 100px;
        }
    }
    &__social {
        & a + a {
            margin-left: 8px;
        }
    }
    &__menu {
        height: 100vh;
        width: 100vw;
        background-color: $mainColor;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        opacity: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        transition: all .5s ease;
        & li {
            text-align: center;
            font-size: 20px;
        }
        & li + li {
            margin-top: 40px;
        }
    }
    @media (min-width: $mobile-max) {
    }
    @media (min-width: $tablet-min) {
        &__container {
            flex-direction: row;
        }
    }
    @media (min-width: $tablet-max) {
    }
    @media (min-width: 1200px) {
        height: 64px;
        &__burger {
            display: none;
        }
        &__menu {
            display: flex;
            align-items: center;
            justify-content: space-between;
            max-width: 67%;
            height: auto;
            flex-direction: row;
            position: relative;
            & li {
                font-size: 16px;
            }
            & li + li {
                margin-top: 0;
            }
        }
        &.scroll {
            height: 64px;
            .header__logo {
                transition: all .5s;
                &::after {
                    transition: all .5s;
                    height: 64px;
                }
                & svg {
                    left: 0;
                    top: 0;
                    width: 100px;
                    transform: translateY(-50%);
                    transition: all .5s;
                }
            }
        }
        &__container {
            position: relative;
            display: flex;
            align-items: center;
            justify-content: space-between;
            height: 100%;
        }
        &__logo {
            position: relative;
            margin-right: 37px;
            transition: all .5s;
            left: 0;
            transform: none;
            height: auto;
            width: 200px;
            &::after {
                height: 111px;
                width: 200px;
                left: 0;
                top: -40px;
                z-index: -1;
            }
            &:hover {
                cursor: pointer;
            }
            & svg {
                transition: all .5s;
                position: absolute;
                top: 15px;
                left: 50%;
                z-index: 1;
                transform: translate(-50%, -50%);
                & path {
                    &.fil0 {
                        fill: $mainColor;
                    }
                }
            }
        }
        &__social {
            display: flex;
            margin-left: 91px;
            margin-right: 12px;
            max-width: 114px;
            width: 100%;
            justify-content: center;
            & a {
                display: block;
                color: inherit;
                transition: all .5s;
                &:hover {
                    opacity: .5;
                }
                &:not(:last-child) {
                    margin-right: 15px;
                }
            }
        }
    }
}

.menu {
    &--desktop {
        display: none;
    }
    @media (min-width: 1200px) {
        &--desktop {
            display: flex;
        }
        &--mobile {
            display: none;
        }
    }
}

.fade-leave-to, .fade-enter {
  opacity: 1;
  transition: opacity .3s;
}
.fade-leave-active, .fade-enter-active {
  opacity: 0;
  transition: opacity .3s;
}
</style>
