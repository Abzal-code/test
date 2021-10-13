<template>
  <div class="cart">
    <div class="col-3">
      <label class="sr-only" for="inlineFormInputName2">Количество</label>
      <input type="number" v-model="quantity" class="form-control mb-2 mr-sm-2" />
    </div>
    <button
      v-if="!isInCardProp"
      @click.stop="addCart({product, quantity})"
      type="button"
      class="btn btn-primary btn-lg btn-block col-9"
    >Добавить в корзину</button>
    <button
      v-else
      @click.stop="removeCart(product.id)"
      type="button"
      class="btn btn-primary btn-lg btn-block col-9"
    >Удалить с корзины</button>
    <a href="#" class="btn btn-primary btn-lg btn-block">Купить</a>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
export default {
  props: ["product"],
  data() {
    return {
      isInCardProp: false,
      quantity: 1,
    };
  },
  computed: {
    ...mapState("product", ["cart"]),
  },
  methods: {
    ...mapActions("product", ["addCart", "removeCart"]),

    isInCart(id) {
      for (let index = 0; index < this.cart.length; index++) {
        const element = this.cart[index];
        if (element.id === id) {
          return true;
        }
      }
      return false;
    },
  },
  watch: {
    product(val) {
      this.isInCardProp = this.isInCart(val.id);
    },
    cart() {
      this.isInCardProp = this.isInCart(this.product.id);
    },
    quantity(val) {
      if (val <= 0) {
        this.quantity = 1;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.cart {
  display: flex;
  flex-direction: row;
  margin-top: 32px;
  width: 70%;
  .col-3 {
    padding-left: 0;
    input {

    }
  };
  button {
    background: #E01563;
    border-radius: 4px;
    height: 50px;
  };
  a {
    position: relative;
    top: -8px;
    background: #393434;
    border-radius: 4px;
    margin-left: 20px;
    height: 50px;
    width: 200px;
  }
}
</style>
