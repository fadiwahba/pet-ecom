<template>
  <div class="navbar__cart ml-4">
    <button class="navbar__cart-icon" @click="showCart = !showCart">
      <i class="fas fa-shopping-cart fa-2x"></i>
      <transition name="slide-fade" mode="out-in">
        <span :key="cartItems.length" class="total-quantity">
          {{ cartItems.length }}
        </span>
      </transition>
    </button>
    <div v-if="showCart" class="cart-dropdown">
      <ul class="list-group list-group-flush">
        <li
          v-for="(item, index) in cartItems"
          :key="index"
          class="list-group-item d-flex justify-content-between align-items-center"
        >
          <span>
            <img
              :src="item.product_image"
              :alt="item.display_name"
              class="cart-dropdown-img pr-2"
            />
          </span>
          {{ item.display_name }}
          <button @click="onRemoveFromCart(item)" class="cart-remove-item">
            <i class="far fa-trash-alt"></i>
          </button>
        </li>
        <li
          class="list-group-item d-flex justify-content-between align-items-center"
        >
          <button
            :disabled="cartItems.length === 0"
            class="btn btn-block  btn-lg btn-primary"
          >
            Checkout
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "CartComponent",
  props: {
    cartItems: [Array]
  },
  data() {
    return {
      showCart: false
    };
  },
  methods: {
    onRemoveFromCart(item) {
      this.$emit("remove-cart-item", item);
    }
  }
};
</script>

<style lang="scss">
.navbar {
  &__cart-icon {
    color: #ffffff;
    border: none;
    background: none;
  }
  &__cart {
    position: relative;

    .total-quantity {
      align-items: center;
      background: #1de9b6;
      color: #333333;
      border-radius: 50%;
      display: flex;
      font-size: 12px;
      font-weight: bold;
      height: 25px;
      width: 25px;
      justify-content: center;
      padding: 0.5rem;
      position: absolute;
      right: -10px;
      top: -5px;
    }

    .cart-dropdown {
      background: white;
      border: 1px solid lightgray;
      border-radius: 5px;
      box-shadow: 0 0 2px rgba(0, 0, 0, 0.2);
      color: #333;
      font-size: 1.3rem;
      overflow: auto;
      padding: 0 1rem;
      position: absolute;
      right: 0;
      max-width: 400px;
      max-height: 600px;
      z-index: 100;
      min-width: 330px;

      .cart-remove-item {
        color: salmon;
        margin-left: 2rem;
        background: none;
        border: 0;
        cursor: pointer;
      }
    }
    .cart-dropdown-img {
      max-width: 50px;
    }
  }
}

.slide-fade-enter-active {
  transition: all 0.2s ease;
}
.slide-fade-leave-active {
  transition: all 0.2s;
}
.slide-fade-enter,
.slide-fade-leave-to {
  transform: scale(2);
}
</style>
