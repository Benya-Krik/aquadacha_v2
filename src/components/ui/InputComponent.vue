<template>
    <input class="input" :class="`input--${modificator}`" :placeholder="placeholder" @focus="isChecked(radioId)"/>
</template>

<script>
export default {
  props: ['placeholder', 'modificator', 'radioId'],
  methods: {
    isChecked (id) {
      document.querySelector(id).checked = true
    }
  }
}
</script>

<style lang="scss" scoped>
.input {
    border: 1px solid #D9D9D9;
    border-radius: 100px;
    padding: 24px 20px 24px 38px;
    max-height: 70px;
    width: 100%;
    outline: none;
    position: relative;
    &::placeholder {
        color: #BBBBBB;
        font-size: 16px;
        line-height: 22px;
    }
    &--withRadio {
        padding-left: 60px;
        max-height: 64px;
    }
}
</style>
