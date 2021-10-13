<template>
  <div class="section">
    <div class="products__container">
      <div class="header">
        <img src="@/assets/header.png" alt="">
        <div class="text">
          <h3>Название Заголовка</h3>
          <p>Мини-описание</p>
          <img src="@/assets/circle.svg" alt="">
        </div>
      </div>
      <h2>Активационные товары</h2>
      <div class="row">
        <div class="col-md-2" v-for="product in products.slice(0, 12)" :key="product.id">
          <ProductCard :product="product" />
        </div>
      </div>
      <div class="wrapper__bonus">
        <h2>Бонусные товары</h2>
        <div class="row">
          <div class="col-md-2" v-for="product in products.slice(6, 18)" :key="product.id">
            <ProductCard :product="product" />
          </div>
        </div>
        <div class="row">
          <a class="btn" href="#">Перейти ко всем категориям</a>
        </div>
      </div>
      <div class="carousel">
        <div class="row">
          <div style="width:100%;margin:20px auto;height:300px">
            <!-- Using the slider component -->
            <slider ref="slider" :options="options">
              <!-- slideritem wrapped package with the components you need -->
              <slideritem>
                <img src="@/assets/slider.jpg" alt="">
              </slideritem>
              <slideritem>
                <img src="@/assets/slider1.jpg" alt="">
              </slideritem>
              <!-- Customizable loading -->
              <div slot="loading">loading...</div>
            </slider>
          </div>
        </div>
      </div>
    </div>
    <div class="sponsor">
      <img src="@/assets/sponsors.png" alt="">
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
import ProductCard from "../../components/products/ProductCard";
import { slider, slideritem } from 'vue-concise-slider'
export default {
  data() {
    return {
      //Slider configuration [obj]
      options: {
        currentPage: 0,
        thresholdDistance: 500,
        thresholdTime: 100,
        autoplay:1500,
        loop:true,
        loopedSlides:1,
        slidesToScroll:1
      }
    }
  },
  computed: {
    ...mapGetters("product", ["products"]),

  },
  components: {
    ProductCard,
    slider,
    slideritem
  },
  methods: {
    ...mapActions("product", ["getProducts", "addCart", "removeCart"]),
  },
  mounted() {
    this.getProducts();
  }
};
</script>

<style scoped lang="scss">
.section {
  .products__container {
    display: flex;
    flex-direction: column;
    width: 100%;
    .header {
      max-width: 1140px;
      width: 100%;
      position: relative;
      margin: 0 auto;
      img {
        width: 100%;
      }
      .text {
        background-color: #FFFFFF;
        border-radius: 4px;
        width: 524px;
        height: 127px;
        position: absolute;
        bottom: 35px;
        left: 45px;
        h3 {
          margin-left: 32px;
          margin-top: 22px;
          font-family: Gilroy;
          font-style: normal;
          font-weight: 600;
          font-size: 24px;
          line-height: 22px;
        }
        p {
          margin-left: 32px;
          font-family: Gilroy;
          font-style: normal;
          font-weight: normal;
          font-size: 18px;
          line-height: 22px;
          /* identical to box height, or 125% */
          letter-spacing: -0.24px;
          color: rgba(29, 26, 26, 0.57);
        }
        img {
          width: 50px;
          margin-left: 32px;
        }
      }

    }
    h2 {
      margin-top: 54px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: Gilroy;
      font-style: normal;
      font-weight: 600;
      font-size: 36px;
      line-height: 45px;
      letter-spacing: -0.24px;
      color: #232020;
    }
    .row {
      margin: 0 auto;
      margin-top: 50px;
      max-width: 1140px;
      width: 100%;
    }
  }
  .wrapper__bonus {
    background-color: #F0F0F0;
    width: 100%;
    margin-top: 60px;;
    h2 {
      margin-top: 54px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: Gilroy;
      font-style: normal;
      font-weight: 600;
      font-size: 36px;
      line-height: 45px;
      letter-spacing: -0.24px;
      color: #232020;
    }
    .row {
      width: 1140px;
      .col-md-2 {
        width: 168px;
        height: 239px;
        margin-top: 35px;
      }
    }
    .row {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 1140px;
      .btn {
        text-decoration: none;
        background-color: #7DC1D7;
        color: #ffffff;
        margin: 56px 0;
      }
    }
  }
  .carousel {
    max-width: 1140px;
    margin: 0 auto;
    width: 100%;
  }
  .sponsor {
    background-color: #CDF3FF;
    width: 100%;
    height: 154px;
    position: relative;
    img {
      width: 70%;
      position: absolute;
      left: 15%;
      top: 25%;
    }
  }
}
</style>
