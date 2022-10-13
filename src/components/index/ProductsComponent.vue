<template>
    <section class="products" id="products">
        <div class="products__container container">
            <h2 class="products__title title title--bold">Наша продукция - все, что необходимо вашему бассейну!</h2>
            <p class="products__description">В нашем ассортименте на данный момент 6 средств - каждое из них обладает своим эффектом и предназначено для определенно этапа очистки бассейна.</p>
            <ul class="products__list" >
                <product-card
                  v-for="(item, index) in products" :key="index"
                  :image="item.image"
                  :title="item.title"
                  :description="item.description"
                  :price="item.price"
                  :weight="item.weight"
                  @toggle-popup="togglePopup(item)"
                />
            </ul>
        </div>
        <popup-component
          :isOpened="isOpened"
          :dataPopup="dataPopup"
          :isProductPopup="true"
          @toggle-popup="togglePopup"
        />
    </section>
</template>

<script>
import ProductCard from '../blocks/ProductCard.vue'
import PopupComponent from '../blocks/PopupComponent.vue'
export default {
  components: {
    ProductCard,
    PopupComponent
  },
  data () {
    return {
      products: [
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        },
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        },
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        },
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        },
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        },
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        },
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        },
        {
          image: '/images/products/product.png',
          title: 'Дезинфектор кальций-хлор 92%',
          description: 'Для дезинфекции воды и санитарной обработки',
          price: '1500',
          weight: '1',
          benefit: 'Экономичная упаковка - хватит на весь сезон!',
          specification: [
            {
              title: 'Область применения:',
              text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
            },
            {
              title: 'Как применять:',
              text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
            },
            {
              title: 'Фасовка:',
              text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
            }
          ]
        }
      ],
      isOpened: false,
      dataPopup: {},
      isProductPopup: false
    }
  },
  methods: {
    togglePopup (data) {
      this.isOpened = !this.isOpened
      document.querySelector('html').classList.toggle('opened')
      if (data) {
        this.dataPopup = data
      }
    }
  }
}
</script>

<style lang="scss" scoped>
    .products {
      background: url(@/assets/images/products/background.png);
      background-size: cover;
      &__container {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 48px;
        padding-bottom: 72px;
      }
      &__title {
        text-align: center;
      }
      &__description {
        text-align: center;
        margin-top: 24px;
        margin-bottom: 46px;
      }
      &__list {
        display: grid;
        grid-template-columns: 1fr;
        grid-row-gap: 26px;
        width: 100%;
      }
      @media (min-width: $tablet-min) {
        &__list {
          grid-template-columns: 1fr 1fr;
          grid-column-gap: 24px;
          grid-row-gap: 24px;
        }
        &__title {
          max-width: 500px;
        }
        &__description {
          max-width: 700px;
        }
      }
      @media (min-width: $desktop) {
        &__container {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding-top: 80px;
            padding-bottom: 211px;
        }
        &__title {
            max-width: 916px;
            text-align: center;
        }
        &__description {
            max-width: 833px;
            text-align: center;
            margin-top: 24px;
            margin-bottom: 46px;
        }
        &__list {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr 1fr;
            grid-column-gap: 27px;
            grid-row-gap: 26px;
        }
      }
    }
</style>
