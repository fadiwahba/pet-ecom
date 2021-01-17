<template>
  <div>
    <h2 class="mt-0">Filters</h2>
    <div class="card mb-4">
      <div class="card-header">
        Sort by
      </div>
      <div class="card-body">
        <div class="form-group">
          <label for="sortBySelectControl">
            Example select
          </label>
          <select class="form-control" id="sortBySelectControl">
            <option>Relevance</option>
            <option>Lowest Price</option>
            <option>Highest Price</option>
            <option>Lowest Rating</option>
            <option>Highest Rating</option>
            <option>Lowest Reviews</option>
            <option>Highest Reviews</option>
          </select>
        </div>
      </div>
    </div>
    <div class="card mb-4">
      <div class="card-header">
        Color
      </div>
      <div class="card-body">
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="productColor"
            id="productColor1"
            value="all"
            checked
          />
          <label class="form-check-label" for="productColor1">
            All
          </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="productColor"
            id="productColor2"
            value="brown"
          />
          <label class="form-check-label" for="productColor1">
            Brown
          </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="productColor"
            id="productColor3"
            value="grey"
          />
          <label class="form-check-label" for="productColor2">
            Grey
          </label>
        </div>
      </div>
    </div>
    <div class="card mb-4">
      <div class="card-header">
        Size
      </div>
      <div class="card-body">
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="productSize"
            id="productSize1"
            value="all"
            checked
          />
          <label class="form-check-label" for="productSize1">
            All
          </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="productSize"
            id="productSize2"
            value="small"
          />
          <label class="form-check-label" for="productSize1">
            Small
          </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="productSize"
            id="productSize3"
            value="medium"
          />
          <label class="form-check-label" for="productSize2">
            Medium
          </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="productSize"
            id="productSize4"
            value="large"
          />
          <label class="form-check-label" for="productSize3">
            Large
          </label>
        </div>
      </div>
    </div>
    <div class="card mb-4">
      <div class="card-header">
        Price
      </div>
      <div class="card-body">
        <label for="customRange2">$10 - $100</label>
        <input
          type="range"
          class="custom-range"
          min="10"
          max="100"
          step="10"
          id="priceRangeControl"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FiltersComponent"
};
</script>

<style lang="scss"></style>
