<template>
  <div class="products__wrapper">
    <section class="row">
      <div
        v-for="(product, index) in productList"
        :key="index"
        class="col-sm-12 col-md-4"
      >
        <div class="card mb-4">
          <img
            :src="product.product_image"
            :alt="product.display_name"
            class="card-img-top"
          />
          <div class="card-body">
            <h5 class="card-title text-truncate" :title="product.display_name">
              {{ product.display_name }}
            </h5>
            <hr />
            <div class="meta-data">
              <a
                href="#"
                class="text-info mr-2 mr-2"
                :title="product.category + ' category'"
              >
                <i class="fas fa-tag fa-xs"></i> {{ product.category }}
              </a>
              <a href="#" class="text-warning mr-2" title="Rating">
                <i class="fas fa-star fa-xs"></i> {{ product.avg_rating }}
              </a>
              <a href="#" class="text-success mr-2" title="Reviews">
                <i class="fas fa-comment-alt fa-xs"></i> {{ product.reviews }}
              </a>
            </div>
            <div
              v-if="product.varieties && product.varieties.length"
              class="varieties"
            >
              <hr />
              <div
                v-for="(option, i) in product.varieties"
                :key="i"
                class="form-check d-flex justify-content-between"
              >
                <span>
                  <input
                    class="form-check-input"
                    type="radio"
                    :name="product.name + '-sizeRadioControl'"
                    :id="product.name + '-sizeRadioControl'"
                    :value="product.name"
                    :checked="i === 0"
                  />
                  <label
                    class="form-check-label"
                    :for="product.name + '-sizeRadioControl'"
                  >
                    {{ option.size }} ({{ option.colour }})
                  </label>
                </span>
                <span>
                  <strong class="ml-2">
                    {{ option.currency }}${{ option.price }}
                  </strong>
                </span>
              </div>
            </div>
            <hr />
            <div class="d-flex justify-content-between">
              <button
                @click="$emit('add-to-cart', product)"
                class="btn btn-secondary"
              >
                Add to cart <i class="fas fa-cart-plus"></i>
              </button>
              <button class="btn btn-link">
                Details <i class="fas fa-chevron-right"></i>
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "ProductsComponent",
  props: {
    productList: Array
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss"></style>
