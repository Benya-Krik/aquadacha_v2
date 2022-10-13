<template>
    <main>
        <main-component v-if="main"/>
        <benefits-component v-if="benefits"/>
        <products-component v-if="products"/>
        <banner-form v-if="banner"/>
        <problems-component v-if="problems"/>
        <banner-instruction v-if="banner2"/>
    </main>
</template>

<script>
import MainComponent from '../index/MainComponent.vue'
import BenefitsComponent from '../index/BenefitsComponent.vue'
import ProductsComponent from '../index/ProductsComponent.vue'
import BannerForm from '../index/BannerForm.vue'
import ProblemsComponent from '../index/ProblemsComponent.vue'
import BannerInstruction from '../index/BannerInstruction.vue'

export default {
  components: {
    MainComponent,
    BenefitsComponent,
    ProductsComponent,
    BannerForm,
    ProblemsComponent,
    BannerInstruction
  },
  data () {
    return {
      main: true,
      benefits: true,
      products: true,
      banner: true,
      problems: true,
      banner2: true
    }
  }
}
</script>
