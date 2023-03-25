<template>
  <div>
    <h1>Welcome to My Skincare Shop</h1>
    <ProductList :products="products" :categories="categories" @filter-products="updateCategoryFilter" />
  </div>
</template>



<script>
import ProductList from '@/components/ProductList.vue';

export default {
  components: {
    ProductList
  },
  data() {
    return {
      products: [
        {
          id: 1,
          name: 'Vitamin C Serum',
          description: 'A powerful antioxidant serum that helps brighten and enhance skin radiance.',
          image: 'https://via.placeholder.com/150x150.png?text=Vitamin+C+Serum',
          price: 35,
          category: 'Serums'
        },
        {
          id: 2,
          name: 'Retinol Cream',
          description: 'A retinol-based cream that helps reduce the appearance of fine lines and wrinkles.',
          image: 'https://via.placeholder.com/150x150.png?text=Retinol+Cream',
          price: 45,
          category: 'Moisturizers'
        },
        {
          id: 3,
          name: 'Hyaluronic Acid Serum',
          description: 'A hydrating serum that helps plump and moisturize the skin.',
          image: 'https://via.placeholder.com/150x150.png?text=Hyaluronic+Acid+Serum',
          price: 25,
          category: 'Serums'
        },
        {
          id: 4,
          name: 'Glycolic Acid Toner',
          description: 'A toner that exfoliates and helps improve the texture of the skin.',
          image: 'https://via.placeholder.com/150x150.png?text=Glycolic+Acid+Toner',
          price: 20,
          category: 'Toners'
        },
        {
          id: 5,
          name: 'SPF 30 Sunscreen',
          description: 'A broad-spectrum sunscreen that protects the skin from UVA and UVB rays.',
          image: 'https://via.placeholder.com/150x150.png?text=SPF+30+Sunscreen',
          price: 15,
          category: 'Sunscreen'
        }
      ],
      categories: [
        {
          id: 1,
          name: 'Moisturizers'
        },
        {
          id: 2,
          name: 'Serums'
        },
        {
          id: 3,
          name: 'Toners'
        },
        {
          id: 4,
          name: 'Sunscreen'
        }
      ],
      selectedCategory: null
    };
  },

  methods: {
    updateCategoryFilter(categoryId) {
      this.selectedCategory = categoryId;
    }
  }
};
</script>
