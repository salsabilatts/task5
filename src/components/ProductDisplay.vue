<template>
  <div :class="['product-container', sectionClass]">
    <div v-if="isLoading" class="loader"></div>

    <div v-else class="product-card">
      <template v-if="product.category !== 'unavailable'">
        <img :src="product.image" alt="product image" class="product-image" />
        <div class="product-details">
          <h2 :class="titleClass">{{ product.title }}</h2>
          <p class="category">{{ product.category }}</p>
          <p class="rating">{{ product.rating.rate }}/5 ⭐</p>
          <hr />
          <p class="description">{{ product.description }}</p>
          <hr />
          <p class="price">${{ product.price }}</p>
          <div class="actions">
            <button :class="['buy-button', buyButtonClass]">Buy now</button>
            <button :class="['next-button', nextButtonClass]" @click="nextProduct">Next product</button>
          </div>
        </div>
      </template>


      <template v-else>
        <div class="product-details unavailable-content">
            <img src="@/assets/style/sad-face.png" alt="Unavailable" class="unavailable-image" />
            <div class="overlay-content">
                <h2>Product Not Available</h2>
                <button :class="['next-button', buttonClass]" @click="nextProduct">Next product</button>
            </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 1,
      product: {},
      isLoading: true,
    };
  },
  computed: {
    sectionClass() {
      if (this.product.category === "men's clothing") return 'men-section';
      if (this.product.category === "women's clothing") return 'women-section';
      return 'unavailable-section';
    },
    titleClass() {
    if (this.product.category === "men's clothing") return 'title-men';
    if (this.product.category === "women's clothing") return 'title-women';
    return '';
    },
    buyButtonClass() {
    if (this.product.category === "men's clothing") return 'btn-buy-men';
    if (this.product.category === "women's clothing") return 'btn-buy-women';
    return 'btn-buy-unavailable';
    },
    nextButtonClass() {
    if (this.product.category === "men's clothing") return 'btn-outline-men';
    if (this.product.category === "women's clothing") return 'btn-outline-women';
    return 'btn-outline-unavailable';
    },
  },
  methods: {
    async fetchProduct() {
      this.isLoading = true;
      try {
        const res = await fetch(`https://fakestoreapi.com/products/${this.currentIndex}`);
        const data = await res.json();
        const allowed = ["men's clothing", "women's clothing"];
        if (allowed.includes(data.category)) {
          this.product = data;
        } else {
          this.product = { category: 'unavailable' };
        }
      } catch (err) {
        console.error('Error fetching product:', err);
        this.product = { category: 'unavailable' };
      } finally {
        this.isLoading = false;
      }
    },
    nextProduct() {
      this.currentIndex = this.currentIndex >= 20 ? 1 : this.currentIndex + 1;
      this.fetchProduct();
    },
  },
  mounted() {
    this.fetchProduct();
  },
};
</script>

<style src="@/assets/style/page.css"></style>
