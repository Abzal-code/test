<template>
  <div class="details">
    <div class="bread-crumbs">
      <router-link class="navbar-brand" to="/"><img src="@/assets/arrow.svg" alt=""> Главная</router-link>-
      <a href="#">Личный кабинет</a>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="col-6">
          <div class="card text-left shadow-md">
            <img class="card-img-top" :src="product.imageUrl" alt />
          </div>
          <div class="option_img">
            <img src="@/assets/1.svg" alt="">
            <img src="@/assets/2.svg" alt="">
            <img src="@/assets/3.svg" alt="">
            <img src="@/assets/4.svg" alt="">
          </div>
        </div>
        <div class="col-6 text-left text-justify">
          <div class="type__product">
            <div class="vendor__code">
              <span>085978891</span>
            </div>
            <div class="type-product">
              <span>Одежда</span>
            </div>
            <div :class="product.price > 250 ? 'green' : 'red'">
              <span>{{ product.price > 250 ? 'Новинка'.toUpperCase() : 'Скидка'.toUpperCase() }}</span>
            </div>
          </div>
          <div class="display-3">{{ product.name }}</div>
          <p class="price">{{ product.price }} ₸</p>
          <AddToCart :product="product"  />
          <p class="product-text lead text-justify">{{ product.content }}</p>
          <a href="#" class="btn">Подробнее</a>
        </div>
        <div class="heart-btn">
          <a href="#"><img src="@/assets/heart-product.svg" alt=""></a>
        </div>
      </div>
    </div>
    <div class="container-fluid second-container">
      <div class="row">
        <ul class="tabs" role="tablist">
          <li>
            <input type="radio" name="tabs" id="tab1" checked />
            <label for="tab1"
                   role="tab"
                   aria-selected="true"
                   aria-controls="panel1"
                   tabindex="0">О товаре</label>
            <div id="tab-content1"
                 class="tab-content"
                 role="tabpanel"
                 aria-labelledby="description"
                 aria-hidden="false">
              <div class="content1">
                <img src="@/assets/example.jpg" alt="">
                <p>Мужские костюмы в "Джентльменах" прелесть что такое. Эдакая смесь ретро и современности, британщины и брутальщины.
                  Кстати, в фильме есть несколько моментов, которые можно смело позаимствовать в повседневный стиль. Ибо круто. Костюмы пошиты из классических тканей, имеют современный крой, посадку и расцветки. Все вместе это создает просто великолепный микс.</p>
              </div>
            </div>
          </li>

          <li>
            <input type="radio" name="tabs" id="tab2" />
            <label for="tab2"
                   role="tab"
                   aria-selected="false"
                   aria-controls="panel2"
                   tabindex="0">Характеристики</label>
            <div id="tab-content3"
                 class="tab-content"
                 role="tabpanel"
                 aria-labelledby="specification"
                 aria-hidden="true">
              <p>"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla?</p>
            </div>
          </li>

          <li>
            <input type="radio" name="tabs" id="tab3"/>
            <label for="tab3"
                   role="tab"
                   aria-selected="false"
                   aria-controls="panel3"
                   tabindex="0">Отзывы</label>
            <div id="tab-content4"
                 class="tab-content"
                 role="tabpanel"
                 aria-labelledby="description"
                 aria-hidden="false">
              <p>"Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."</p>
            </div>
          </li>

          <li>
            <input type="radio" name="tabs" id="tab4" />
            <label for="tab4"
                   role="tab"
                   aria-selected="false"
                   aria-controls="panel4"
                   tabindex="0">Доставка</label>
            <div id="tab-content2"
                 class="tab-content"
                 role="tabpanel"
                 aria-labelledby="specification"
                 aria-hidden="true">
              <p>"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla?</p>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
import AddToCart from "../../components/details/AddToCart"
export default {
  data () {
    return {
      isInCardProp: false,
    }
  },
  computed: {
    ...mapGetters("account", ["user"]),
    ...mapGetters("product", ["product"])
  },
  components: { AddToCart },
  methods: {
    ...mapActions("product", ["productDetails"]),
  },
  mounted() {
    this.productDetails(this.$route.params.idProduct);
  }
};
</script>

<style scoped lang="scss">
$background: #D9EFFF;
$tabs-base-color: #ffffff;

.details {
  background-color: #E5E5E5;
  .bread-crumbs {
    width: 1062px;
    margin: 0 auto;
    padding-top: 61px;
    a {
      text-decoration: none;
      font-family: Gilroy;
      font-style: normal;
      font-weight: normal;
      font-size: 15px;
      line-height: 25px;
      letter-spacing: -0.24px;
      color: rgba(0, 0, 0, 0.53);
    }
  }
  .container-fluid {
    max-width: 1140px;
    width: 100%;
    padding: 61px 0;
    .row {
      width: 1062px;
      height: 540px;
      margin: 0 auto;
      background-color: #ffffff;
      border-radius: 5px;
      position: relative;
      .col-6 {
        padding-left: 0;
        position: relative;
        .card {
          width: 475px;
          height: 357px;
          .card-img-top {
            width: 475px;
            height: 357px;
          }
        }
        .option_img {
          position: absolute;
          display: flex;
          flex-direction: row;
          justify-content: space-between;
          width: 293px;
          bottom: 12%;
          left: 20%;
          background: #FFFFFF;
          border: 1px solid #D5D5D5;
          box-sizing: border-box;
          border-radius: 9px;
          padding: 15px;
          img {
            cursor: pointer;
          }
        }
      }
      .text-left {
        position: relative;
        .type__product {
          display: flex;
          flex-direction: row;
          justify-content: space-between;
          width: 55%;
          margin-top: 31px;
          .type-product {
            border: 1px solid;
            font-size: 12px;
            border-radius: 15px;
            width: 80px;
            text-align: center;
            color: #2199DC;
            background-color: #C0E1FF;
            padding: 2px;
          }
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
        }
        .display-3 {
          margin-top: 18px;
          font-family: Gilroy;
          font-style: normal;
          font-weight: 500;
          font-size: 28px;
          line-height: 34px;
          /* or 123% */
          letter-spacing: -0.24px;
          color: #232020;
          background-color: #ffffff;
        }
        .price {
          margin-top: 23px;
          font-family: Gilroy;
          font-style: normal;
          font-weight: bold;
          font-size: 30px;
          line-height: 20px;
          /* identical to box height, or 67% */
          letter-spacing: -0.24px;
          color: #1C1919;
        }
        .product-text {
          margin-top: 34px;
        }
        .btn {
          position: absolute;
          bottom: 32px;
          background-color: #E2E2E2;
          color: #747474;
          width: 182px;
        }
      }
      .heart-btn {
        position: absolute;
        top: 30px;
        right: 30px;
        a {
          img {
          }
        }
      }
    }
  }
  .second-container {
    .row {
      height: 340px;
      h1 {
        font-weight: normal;
        font-size: 40px;
        font-weight: normal;
        text-transform: uppercase;
        float: left;
        margin: 20px 0 100px 10px;
        span {
          font-size: 13px;
          display: block;
          padding-left: 4px;
        }
      }
      .tabs {
        width: 100%;
        float: none;
        list-style: none;
        position: relative;
        text-align: left;
        background-color: #D9EFFF;
        li {
          float: left;
          display: block;
        }
        input[type="radio"] {
          position: absolute;
          top: 0;
          left: -9999px;
        }
        label {
          display: block;
          padding: 14px 21px;
          border-radius: 2px 2px 0 0;
          font-size: 20px;
          font-weight: normal;
          text-transform: uppercase;
          background: #D9EFFF;
          cursor: pointer;
          position: relative;
          &:hover {
            background: darken($tabs-base-color, 10);
          }
        }
        .tab-content{
          z-index: 2;
          display: none;
          overflow: hidden;
          width: 100%;
          font-size: 17px;
          line-height: 25px;
          padding: 25px;
          position: absolute;
          top: 53px;
          left: 0;
          background: #ffffff;
          height: 100%;
          .content1 {
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: center;
            img {

            }
            p {
              margin-left: 55px;
            }
          }
        }
        //The Magic
        [id^="tab"]:checked + label {
          top: 0;
          background: #ffffff;
        }
        [id^="tab"]:checked ~ [id^="tab-content"] {
          display: block;
        }
      }
      p.link {
        clear: both;
        margin: 380px 0 0 15px;
        a {
          text-transform: uppercase;
          text-decoration: none;
          display: inline-block;
          color: #fff;
          padding: 5px 10px;
          margin: 0 5px;
          background-color: darken($tabs-base-color, 15);
          &:hover {
            background-color: darken($tabs-base-color, 20);
          }
        }
      }
    }
  }
}

</style>
