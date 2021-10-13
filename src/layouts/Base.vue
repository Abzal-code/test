<template>
  <div class="layout">
    <div class="nav__container">
      <nav class="navbar navbar-expand-lg">
        <router-link class="navbar-brand" to="/"><img src="../assets/logo.svg" alt=""></router-link>
        <div class="container">
          <input type="text" id="box" placeholder="Поиск" class="search__box">
          <i class="fas fa-search search__icon" id="icon"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
            <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
          </svg></i>
        </div>
        <div class="location">
          <a href="#">
            <img src="@/assets/location.svg" alt="">
            Алматы
          </a>
        </div>
        <div class="ml-auto">
          <div v-if="user.photoURL">
            <img
              :src="user.photoURL"
              class="img-thumbnail profile-image"
              alt
            />
            <router-link class="btn btn-primary my-2 my-sm-0" to="/cart">
              <img
                src="@/assets/cart.svg"
                width="50"
                alt
              />
              <span class="badge badge-danger badge-pill">{{ cart.length }}</span>
            </router-link>
          </div>
          <router-link v-else class="btn btn-primary my-2 my-sm-0" to="/login">Login</router-link>
        </div>
      </nav>
      <hr>
      <nav class="footer__nav">
        <div class="first__block">
          <router-link class="navbar-brand" to="/"><img src="@/assets/yellow.svg" alt=""></router-link>
        </div>
        <div class="second__block">
          <a href="#">Главная</a>
          <a href="#">О компании</a>
          <a href="#"><img src="@/assets/gift.svg" alt="">Бонусная система</a>
          <a href="#">Поддержка</a>
          <a href="#">Контакты</a>
        </div>
        <div class="third__block">
          <a href="#"><img src="@/assets/heart.svg" alt=""></a>
          <a href="#"><img src="@/assets/cart.svg" alt=""></a>
        </div>
      </nav>
    </div>
    <div class="page-container">
      <router-view />
    </div>
    <footer>
      <div class="top__footer">
        <nav>
          <div class="logo__footer">
            <router-link class="navbar-brand" to="/"><img src="../assets/logo.svg" alt=""></router-link>
          </div>
          <div class="text__footer">
            <ul>
              <li><a href="#">О компании</a></li>
              <li><a href="#">Публичная оферта</a></li>
              <li><a href="#">Блог</a></li>
              <li><a href="#">Для партнеров</a></li>
              <li><a href="#">FAQ</a></li>
            </ul>
          </div>
          <div class="social__footer">
            <ul>
              <li><a href="#"><img src="@/assets/Instagram.svg" alt=""></a></li>
              <li><a href="#"><img src="@/assets/Twitter.svg" alt=""></a></li>
              <li><a href="#"><img src="@/assets/vk.svg" alt=""></a></li>
              <li><a href="#"><img src="@/assets/Facebook.svg" alt=""></a></li>
            </ul>
          </div>
        </nav>
      </div>
      <div class="bottom__footer">
        <div class="bottom__wrapper">
          <div class="block">Лучший магазин (с) 2019 Все права защищены. Интернет-магазин</div>
          <div class="block">Политика конфиденциальности</div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  name: "Base",
  computed: {
    ...mapGetters("account", ["user"]),
    ...mapGetters("product", ["cart"])
  },
  methods: {
    toggleShow() {
      let el = document.getElementById("box");
      el.classList.toggle("show");
    }
  }
};
</script>

<style lang="scss" scoped>
.layout {
  .nav__container {
    display: flex;
    flex-direction: column;
    nav {
      max-width: 1140px;
      width: 100%;
      margin: 0 auto;
      padding-top: 20px;
      background-color: #ffffff;
      padding-left: 20px;
      .navbar-brand {
        font-weight: bold;
        font-size: 25px;
        /* font-family: Comic; */
        color: #ffffff !important;
        position: absolute;
        top: 15%;
      }
      .container {
        width: 460px;
        height: auto;
        background-color: #EEEEEE;
        /*   margin: 20vh auto; */
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        border-radius: 5px;
        border-color: #000000;
        padding: 5px;
        .search__box {
          float: left;
          width: 100%;
          height: 1.5rem;
          /*   display: inline; */
          background: none;
          font-size: 15px;
          padding-left: 5px;
          border-radius: 2rem;
          outline: none;
          border: none;
          position: relative;
          opacity: 1;
          transition: all .75s ease-in;
          /*   border: 2px solid tomato; */
          /*   margin-top: 5px; */
        }
        .search__icon {
          box-sizing: border-box;
          //float: right;
          display: inline-block;
          /*   justify-content: center;
            align-items: center; */
          margin-left: .8rem;
          margin-top: 0;
          cursor: pointer;
          position: absolute;
          right: 10px;
          top: 4px;
          color: #000000;
          transition: all .25s ease-in;
          border-radius: 50%;
        }
      }
      .location {
        position: absolute;
        left: 75%;
        top: 30%;
        a {
          text-decoration: none;
          color: #000000;
          img {
            position: relative;
            right: 5px;
          }
        }
      }


      .profile-image {
        width: 50px;
        border-radius: 100% !important;
      }
    }
    hr {
      width: 1140px;
      margin: 0 auto;
    }
    .footer__nav {
      display: flex;
      flex-direction: row;
      position: relative;
      padding-left: 20px;
      .second__block {
        position: absolute;
        left: 30%;
        top: 17px;
        a {
          position: relative;
          margin-right: 50px;
          text-decoration: none;
          color: #000000;
          img {
            position: absolute;
            left: -25px;
          }
        }
      }
      .third__block {
        position: absolute;
        right: 15px;
        top: 15px;
        a {
          margin-left: 10px;
        }
      }
    }
    .page-container {
      padding-top: 81px;
    }
    .btn {
      font-weight: bold;
      background: #CDF3FF;
      border-radius: 14.5px;
      border-color: #CDF3FF;
    }
    .btn:hover {
      background: #00b4b4;
    }
    input {
      border-radius: 0%;
    }
    .btn:focus {
      background: teal;
    }
  }
  .page-container {
    margin-top: 80px;
  }
  footer {
    display: flex;
    flex-direction: column;
    .top__footer {
      display: flex;
      flex-direction: row;
      width: 1140px;
      margin: 50px auto;
      nav {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 100%;
        padding-left: 20px;
        .logo__footer {
        }
        .text__footer {
          ul {
            display: flex;
            flex-direction: row;
            li {
              list-style: none;
              margin: 0 10px;
              a {
                color: #000000;
              }
            }
          }
        }
        .social__footer {
          ul {
            display: flex;
            flex-direction: row;
            li {
              list-style: none;
              margin: 0 10px;
              a {
                color: #000000;
              }
            }
          }
        }
      }
    }
    .bottom__footer {
      background-color: #000000;
      width: 100%;
      .bottom__wrapper {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 1140px;
        margin: 50px auto;
        .block {
          color: #ffffff;
        }
      }
    }
  }
}
</style>
