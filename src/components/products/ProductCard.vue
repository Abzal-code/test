<template>
  <div class="card__wrapper  shadow-sm">


    <router-link
          type="button"
          :to="'/details/' + product.id"
          class="card"
        >
          <div class="card__header">
            <div :class="product.price > 250 ? 'green' : 'red'">
              <span>{{ product.price > 250 ? 'Новинка'.toUpperCase() : 'Скидка'.toUpperCase() }}</span>
            </div>
            <div class="header__img">
              <img src="@/assets/heart.png" alt="">
            </div>
          </div>
          <div class="card__image">
            <img :src="product.imageUrl" class="card-img-top product-image" />
          </div>
      <div class="card-body">
        <h5 class="card-title text-left">{{ product.name }}</h5>
        <span>{{product.price}}</span>
      </div>
        </router-link>
  </div>
</template>

<script>
export default {
    name: "ProductCard",
    props: ["product"]
};
</script>

<style scoped lang="scss">
.card__wrapper {
  width: 168px;
  height: 239px;
  .card {
    text-decoration: none;
    margin-top: 40px;
    .card__header {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      padding: 10px;
      .green {
        border: 1px solid;
        font-size: 12px;
        border-radius: 15px;
        width: 80px;
        text-align: center;
        color: #ffffff;
        background-color: #3EB991;
        padding: 2px;
      }
      .red {
        border: 1px solid;
        font-size: 12px;
        border-radius: 15px;
        width: 80px;
        text-align: center;
        color: #ffffff;
        background-color: #E01563;
        padding: 2px;
      }
      .header__img {

      }
    }
    .card__image {
      padding: 0 10px;
      img {

      }
    }
    .card-body {
      .card-title {
        color: #1C1919;
      }
      span {
        color: #1C1919;
      }
    }
  }
}
</style>
