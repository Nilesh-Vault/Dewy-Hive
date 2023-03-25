<template>
    <div class="product-list">
        <div class="filter">
            <select :value="selectedCategory" @change="$emit('update:selectedCategory', $event.target.value)">

                <option value="">All Categories</option>
                <option v-for="category in categories" :key="category.id" :value="category.id">{{ category.name }}</option>
            </select>
        </div>
        <div class="products">
            <div v-for="product in filteredProducts" :key="product.id" class="product">
                <img :src="product.image" :alt="product.name" />
                <h3>{{ product.name }}</h3>
                <p>{{ product.description }}</p>
                <p>Price: {{ product.price }}</p>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        products: {
            type: Array,
            required: true,
        },
        categories: {
            type: Array,
            required: true,
        },
        selectedCategory: {
            type: String,
            default: "",
        },
    },
    computed: {
        filteredProducts() {
            return this.products.filter((product) => {
                return this.selectedCategory === "" || product.category === this.selectedCategory;
            });
        },
    },
    methods: {
        filterProducts() {
            this.$emit("filter-products", this.selectedCategory);
        },
    },
};
</script>
  
<style>
.product-list {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

.filter {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 20px;
}

.products {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

.product {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 300px;
    margin-bottom: 20px;
    background-color: #f4f4f4;
    padding: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

.product img {
    width: 200px;
    height: 200px;
    object-fit: contain;
    margin-bottom: 10px;
}

.product h3 {
    font-size: 24px;
    margin-bottom: 10px;
}

.product p {
    font-size: 18px;
    margin-bottom: 10px;
}

.product p:last-child {
    font-weight: bold;
    color: #2ecc71;
}
</style>
  