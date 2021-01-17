<template>
  <div
    class="navbar navbar-expand-lg navbar-dark bg-primary shadow-sm sticky-top"
  >
    <div class="container">
      <a href="#" class="navbar-brand d-flex align-items-center mr-4">
        <img
          class="logo"
          src="https://www.petcircle.com.au/petcircle-assets/images/PC-Logo.svg"
          alt="Pet Circle"
        />
      </a>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <a class="nav-link" href="#">
              Home
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" href="#">
              Products <span class="sr-only">(current)</span>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">
              About
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">
              Contact
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">
              My Account <i class="far fa-user"></i>
            </a>
          </li>
        </ul>
      </div>
      <div class="d-flex justify-content-end align-items-center">
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <CartComponent
          :cartItems="cartItems"
          v-on:remove-cart-item="onRemoveCartItem($event)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CartComponent from "@/components/Cart.vue";
export default {
  name: "HeaderComponent",
  components: {
    CartComponent
  },
  props: {
    cartItems: [Array]
  },
  methods: {
    onRemoveCartItem(item) {
      this.$emit("remove-cart-item", item);
    }
  }
};
</script>

<style lang="scss">
.logo {
  vertical-align: middle;
  width: 100px;
  height: auto;
  color: #ffffff;
  margin: 1rem 0;
}

.navbar-dark .navbar-nav .active > .nav-link,
.navbar-dark .navbar-nav .nav-link.active,
.navbar-dark .navbar-nav .nav-link.show,
.navbar-dark .navbar-nav .show > .nav-link {
  color: #1de9b6;
}

.navbar-dark .navbar-nav .nav-link {
  color: #ffffff;
  transition: all 0.35s ease-in-out;
}

.navbar-dark .navbar-nav .nav-link:focus,
.navbar-dark .navbar-nav .nav-link:hover {
  color: #1de9b6;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 5px;
}
</style>
