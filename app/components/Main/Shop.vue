<template>
    <StackLayout class="bg-container">
        <StackLayout>
            <SearchBar v-model="searchProducts" class="search-bar"/>
        </StackLayout>

        <Label text="Categories" class="productTitle"/>
        <ScrollView orientation="horizontal" scrollBarIndicatorVisible="false">
            <StackLayout orientation="horizontal">
                <Label text="All category" class="categoriesItems" />
                <Label v-for="(item, index) in categories" :key="index" :text="item" class="categoriesItems"/>
            </StackLayout>
        </ScrollView>

        <Label text="Featured product" class="productTitle"/>
        <ScrollView>
            <WrapLayout orientation="horizonal">
                <StackLayout class="shopCard" v-for="(product, index) in filteredItems" :key="index">
                    <Image :src="product.image" stretch="aspectFit" class="product-img"/>
                    <Label :text="product.title" class="product-name" @tap="onProductDetails"/>
                    <Label :text="'$' + product.price" class="product-price" />
                    
                    <StackLayout class="cart-favorite-container">
                        <Label text="Add to Cart" class="add-to-cart-btn" />
                        <Image src="~/assets/icons/favorite.png" class="favoriteIcon"/>
                    </StackLayout>

                </StackLayout>
            </WrapLayout>
        </ScrollView>
    </StackLayout>
</template>

<script>

import ProductsDetailsPage from "../Products/ProductsDetails.vue";

export default {
    data() {
        return {
            productItems: [],

            searchProducts: "",
            categories: []
        };
    },
    computed: {
        filteredItems() {
            return this.productItems.filter(product => product.title.toLowerCase().includes(this.searchProducts.toLowerCase()));
        }
    },
    methods: {
        onProductDetails () {
            this.$navigateTo(ProductsDetailsPage);
        }
    },
    mounted() {
        fetch("https://fakestoreapi.com/products/categories")
            .then(response => response.json())
            .then(result => {
                this.categories = result;
        });

        fetch("https://fakestoreapi.com/products")
            .then(response => response.json())
            .then(result => {
            this.productItems = result;
        });
    }
}
</script>

<style scoped>

.bg-container{
    background-color: rgb(252, 243, 244);
}
.search-bar {
  background-color: rgb(252, 231, 234);
  color: rgb(224, 121, 140);
  font-size: 16;
  height: 40;
  margin: 10;
  padding: 5;
}

.productTitle{
    font-weight: bold;
    font-size: 18;
    margin: 5,10;
    color: rgb(224, 121, 140);
}
.categoriesItems {
  background-color: rgb(224, 121, 140);
  color: white;
  border-radius: 20;
  font-size: 14;
  margin: 8 ,4;
  padding: 8,10;
}
.shopCard{
    width: 30.7%;
    border-radius: 6;
    margin: 5;
    padding: 5;
    background: rgb(251, 245, 246);
    box-shadow: 0 3px 6px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
.product-img{
    width: 100%;
    height: 120;
}

.product-name {
    width: 100%;
    font-size: 18;
    font-weight: bold;
    color: rgb(224, 121, 140);
}

.product-price {
    width: 100%;
    font-size: 16;
}
.cart-favorite-container{
    orientation: horizontal;
}
.add-to-cart-btn {
    background-color: #DE6288;
    width: 75%;
    color: #fff;
    height: 25;
    border-radius: 20;
    font-size: 12;
    vertical-align: middle;
    text-align: center;
    margin-right: 5;
}

.favoriteIcon{
    width: 25;
    height: 25;
    padding: 3;
    border-width: 1;
    border-color: #DE6288;
    border-radius: 50%;
}
</style>