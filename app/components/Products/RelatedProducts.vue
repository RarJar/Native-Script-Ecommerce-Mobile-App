<template>
    <StackLayout>
        <Label text="RELATED PRODUCTS" class="productTitle" />
        <ScrollView orientation="horizontal" scrollBarIndicatorVisible="false">
            <StackLayout orientation="horizontal">
                <StackLayout class="product-card" v-for="(product, index) in relatedProducts" :key="index">
                    <Image :src="product.image" stretch="aspectFit" class="product-img" />
                    <Label :text="product.title" class="product-name" />
                    <Label :text="'$' + product.price" class="product-price" />

                    <StackLayout class="cart-favorite-container">
                        <Label text="Add to Cart" class="add-to-cart-btn" />
                        <Image src="~/assets/icons/favorite.png" class="favoriteIcon"/>
                    </StackLayout>
                </StackLayout>
            </StackLayout>
        </ScrollView>
    </StackLayout>
</template>

<script>

export default {
    data() {
        return {
            relatedProducts: []
        };
    },
    mounted() {
        fetch("https://fakestoreapi.com/products")
            .then(response => response.json())
            .then(result => {
                this.relatedProducts = result;
            });
    }
}
</script>

<style scoped>
.productTitle {
    font-weight: bold;
    font-size: 18;
    color: rgb(224, 121, 140);
    margin-bottom: 10;
}

.product-card {
    width: 130;
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
    font-size: 17;
    font-weight: bold;
    color: rgb(224, 121, 140);
}

.product-price {
    width: 100%;
    font-size: 15;
    margin-bottom: 5;
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
