<template>
  <div class="header">
    <!-- Logo with link back to homepage -->
    <a href="#" class="logo"><LogoIcon /></a>

    <!-- Navigational menu -->
    <nav class="nav">
      <a href="#" class="nav__link">Shop</a>
      <a href="#" class="nav__link">Contact</a>
      <a href="#" class="nav__link">Log In</a>
    </nav>

    <!-- Shopping Bag Icon // toggles cart preview on click -->
    <div class="shopping-cart" @click="toggle_cart">
      <ShoppingBagIcon class="shopping-cart__icon" />
      <span class="shopping-cart__item-count">0</span>
    </div>

    <!-- Cart Preview Card // lists all items in cart with link to checkout -->
    <div class="cart-preview" v-show="show_cart">
      <div class="cart-preview__items">
        <span class="cart-preview__empty-message">Cart is empty</span>
      </div>
      <a href="#" class="btn btn--bottom">Checkout</a>
    </div>
    
  </div>
</template>


<script>
import LogoIcon from "../assets/logo.svg?inline";
import ShoppingBagIcon from "../assets/shopping-bag.svg?inline";

export default {
  name: "Header",
  data: function () {
    return { show_cart: false };
  },
  methods: {
    toggle_cart: function () {
      this.show_cart = !this.show_cart;
    },
  },
  components: {
    LogoIcon,
    ShoppingBagIcon,
  },
};
</script>


<style lang="scss" scoped>
.header {
  align-items: center;
  display: flex;
  height: 70px;
  justify-content: space-between;
  margin-bottom: 25px;
  width: 100%;
  @media screen and (max-width: 800px) {
    height: 60px;
    margin-bottom: 20px;
    padding: 10px;
  }
}

.logo {
  padding: 25px;
  @media screen and (max-width: 800px) {
    padding: 0;
    width: 50px;
  }
}

.nav {
  align-items: center;
  display: flex;
  flex: 1;
  height: 100%;
  justify-content: flex-end;

  &__link {
    cursor: pointer;
    padding: 10px 15px;
    text-transform: uppercase;
  }
}

.shopping-cart {
  align-items: center;
  cursor: pointer;
  display: flex;
  height: 45px;
  justify-content: center;
  position: relative;
  width: 45px;

  &__icon {
    height: 24px;
    width: 24px;
  }

  &__item-count {
    bottom: 12px;
    font-size: 10px;
    font-weight: bold;
    position: absolute;
  }
}

.cart-preview {
  background-color: white;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  height: 340px;
  padding: 20px;
  position: absolute;
  right: 40px;
  top: 90px;
  width: 240px;
  z-index: 5;

  &__items {
    display: flex;
    flex-direction: column;
    height: 240px;
    overflow-y: auto;
  }

  &__empty-message {
    font-size: 18px;
    margin: 50px auto;
  }
}

.btn {
  background-color: black;
  border: none;
  color: white;
  cursor: pointer;
  display: flex;
  font-family: "Oswald", sans-serif;
  font-size: 15px;
  font-weight: bolder;
  height: 50px;
  justify-content: center;
  letter-spacing: 0.5px;
  line-height: 50px;
  min-width: 165px;
  padding: 0 35px 0 35px;
  text-transform: uppercase;
  width: auto;

  &--bottom {
    margin-top: auto;
  }

  &:hover {
    background-color: white;
    border: 1px solid black;
    color: black;
  }

  &--inverted {
    background-color: white;
    border: 1px solid black;
    color: black;

    &:hover {
      background-color: black;
      border: none;
      color: white;
    }
  }
}
</style>