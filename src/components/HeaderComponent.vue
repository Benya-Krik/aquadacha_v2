<template>
    <header class="header">
        <div class="header__container container">
            <div class="header__logo">
                <logo-component />
            </div>
            <div class="header__menu"></div>
            <div class="header__social"></div>
        </div>
    </header>
</template>

<script>
import LogoComponent from './ui/LogoComponent.vue'
export default {
  components: {
    LogoComponent
  }
}
</script>

<style lang="scss" scoped>
.header {
    background-color: $mainColor;
}
</style>
