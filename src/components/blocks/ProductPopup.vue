<template>
    <h3 class="product-popup__title title title--bold">{{dataPopup.title}}</h3>
    <p class="product-popup__benefit">{{dataPopup.benefit}}</p>
    <div class="product-popup__content">
        <div class="product-popup__left">
            <div class="product-popup__image">
                <img :src="dataPopup.image" alt="">
            </div>
        </div>
        <div class="product-popup__right">
            <ul class="product-popup__list">
                <li v-for="(item, index) in dataPopup.specification" :key="index">
                    <h4 class="product-popup__title title title--small">{{item.title}}</h4>
                    <p>{{item.text}}</p>
                </li>
            </ul>
        </div>
    </div>
    <div class="product-popup__buy">
        <p class="product-popup__price">
            Цена: <span class="green"> {{dataPopup.price}} руб</span>
        </p>
        <button-default
            class="product-popup__button"
            :color="'green'"
            :text="'Купить'"
        />
    </div>
</template>

<script>
import ButtonDefault from '../ui/ButtonDefault.vue'
export default {
  props: ['dataPopup'],
  components: {
    ButtonDefault
  }
}
</script>

<style lang="scss" scoped>
.product-popup {
    &__title {
        margin-bottom: 8px;
        text-align: center;
    }
    &__content {
        margin-top: 48px;
    }
    &__right {
        margin-top: 16px;
        & h4 {
            text-align: left;
        }
        & li + li {
            margin-top: 8px;
        }
    }
    &__button {
        width: 100%;
        margin-top: 12px;
    }
    &__price {
        text-align: center;
        & span.green {
            color: $mainColor;
            font-size: 24px;
        }
    }
    &__buy {
        display: flex;
        flex-direction: column;
        margin-top: 32px;
    }
    &__image {
        width: 100%;
        & img {
            width: 100%;
        }
    }
    &__benefit {
        text-align: center;
    }
    @media (min-width: $tablet-min) {
        &__title {
            max-width: 70%;
            margin-bottom: 8px;
            text-align: left;
        }
        &__benefit {
            text-align: left;
        }
        &__content {
            display: flex;
            align-items: center;
            margin-top: 48px;
        }
        &__left {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin-right: 40px;
        }
        &__right {
            & li + li {
                margin-top: 8px;
            }
        }
        &__button {
            max-width: 200px;
        }
        &__price {
            width: 270px;
            margin-right: 40px;
            text-align: center;
            & span.green {
                color: $mainColor;
                font-size: 24px;
            }
        }
        &__buy {
            flex-direction: row;
            align-items: center;
        }
        &__image {
            width: 270px;
        }
    }
    @media (min-width: $desktop) {
        &__title {
            max-width: 70%;
            margin-bottom: 8px;
        }
        &__content {
            display: flex;
            align-items: center;
            margin-top: 48px;
        }
        &__left {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin-right: 40px;
        }
        &__right {
            & li + li {
                margin-top: 8px;
            }
        }
        &__button {
            max-width: 200px;
        }
        &__price {
            width: 270px;
            margin-right: 40px;
            text-align: center;
            & span.green {
                color: $mainColor;
                font-size: 24px;
            }
        }
        &__buy {
            display: flex;
        }
        &__image {
            width: 270px;
        }
    }
}
</style>
