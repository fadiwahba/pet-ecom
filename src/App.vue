<template>
  <div id="app">
    <div class="layout">
      <HeaderComponent
        v-bind:cartItems="addToCartList"
        v-on:remove-cart-item="onRemoveCartItem($event)"
      />

      <div class="flex-grow-1">
        <div class="container">
          <BreadcrumbComponent />

          <h1 class="display-4 text-primary">
            Dog & Puppy Toys (Best Sellers)
          </h1>
          <hr />
          <div class="row">
            <div class="col-sm-12 col-md-3">
              <FiltersComponent />
            </div>
            <div class="col-sm-12 col-md-9">
              <div v-if="isLoading" class="d-flex justify-content-center">
                <div class="spinner-border text-primary m-4" role="status">
                  <span class="sr-only">Loading...</span>
                </div>
              </div>
              <ProductsComponent
                :productList="products"
                v-on:add-to-cart="onAddToCart($event)"
              />
            </div>
          </div>
          <PaginationComponent />
        </div>
      </div>

      <FooterComponent />
    </div>
  </div>
</template>

<script>
import HeaderComponent from "@/components/Header.vue";
import BreadcrumbComponent from "@/components/Breadcrumb.vue";
import FiltersComponent from "@/components/Filters.vue";
import ProductsComponent from "@/components/Products.vue";
import PaginationComponent from "@/components/Pagination.vue";
import FooterComponent from "@/components/Footer.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderComponent,
    BreadcrumbComponent,
    FiltersComponent,
    ProductsComponent,
    PaginationComponent,
    FooterComponent
  },
  data() {
    return {
      isLoading: true,
      products: [],
      addToCartList: []
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      let config = {
        headers: {
          Accept: "application/vnd.github.mercy-preview+json"
        }
      };
      let url =
        "https://run.mocky.io/v3/7f80988c-079f-4712-9d94-ba793bc31895?mocky-delay=1s";

      this.isLoading = true;
      axios.get(url, config).then(response => {
        if (response && response.data) {
          console.log("response: ", response);
          this.products = response.data;
          this.isLoading = false;
        }
      });
    },
    onAddToCart(event) {
      this.addToCartList.push(event);
    },
    onRemoveCartItem(item) {
      this.addToCartList = this.addToCartList.filter(product => {
        return product.name !== item.name;
      });
    }
  }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  font-weight: normal;
  margin: 0;
  padding: 0;
}

html,
body {
  font-family: "Nunito", sans-serif;
  font-size: 14px;
  line-height: 1.5;
  height: 100vh;
  margin: 0;
}

a:hover,
a:active,
a:focus,
i:focus,
i:hover,
i:active,
button:focus {
  text-decoration: none;
  outline: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  color: #1de9b6;
  // font-family: "Bebas Neue", cursive;
  margin: 2rem 0;
}

#app {
  height: 100%;
}

.layout {
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
  height: 100%;

  .flex-grow-1 {
    flex-grow: 1;
  }
}

// Override Bootstrap
.btn {
  transition: all 0.3s ease-in-out;
}
.btn-primary {
  background-color: #1a237e;
  border-color: #1a237e;
}
.text-primary {
  color: #1a237e !important;
}
.bg-primary {
  background-color: #1a237e !important;
}
.btn-primary.disabled,
.btn-primary:disabled {
  background-color: gray;
  border-color: gray;
}
.btn-secondary {
  color: #333;
  background-color: #1de9b6;
  border-color: #1de9b6;
}
.btn-secondary:hover,
.btn-secondary:focus,
.btn-secondary:active {
  color: #333;
  background-color: #1dffc7;
  border-color: #1dffc7;
}

.btn-link {
  font-weight: 400;
  color: #007bff;
  text-decoration: none;
}
</style>
