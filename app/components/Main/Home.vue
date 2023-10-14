<template>
    <StackLayout class="bg-container">

        <Image src="~/assets/images/cover.png" class="coverImg" stretch="aspectFit" />

        <Label text="Categories" class="productTitle"/>
        <ScrollView orientation="horizontal" scrollBarIndicatorVisible="false">
            <StackLayout orientation="horizontal">
                <Label text="All category" class="categoriesItems" />
                <Label v-for="(item, index) in categories" :key="index" :text="item" class="categoriesItems"/>
            </StackLayout>
        </ScrollView>

        <Label text="Featured product" class="productTitle"/>
        <StackLayout>
            <SearchBar class="search-bar"/>
        </StackLayout>
        <ListView for="item in items">
                    <v-template>
                        <StackLayout class="product-item">
                            <Image :src="item.image" stretch="aspectFit" width="50%"/>
                            <Label :text="item.title" class="product-name"/>
                            <Label :text="'$' + item.price" class="product-price" />
                            <Label :text="item.description" class="product-price" />
                            <WrapLayout>
                                <Button text="Add to Cart" class="add-to-cart-btn"/>
                                <Button text="Favorite" class="add-to-favorite-btn"/>
                            </WrapLayout>
                        </StackLayout>
                    </v-template>
                </ListView>
    </StackLayout>
</template>

<script>

    export default {
    data() {
        return {
            categories: [],
            items: []
        };
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
            this.items = result;
        });
    }
};
</script>

<style scoped>

.bg-container{
    background-color: rgb(252, 239, 240);
}
.categoriesItems {
  background-color: rgb(224, 121, 140);
  color: white;
  border-radius: 20;
  font-size: 14;
  margin: 8 ,4;
  padding: 8,10;
}

.coverImg{
    margin: 0 , 5;
    border-radius: 5;
}
.productTitle{
    font-weight: bold;
    font-size: 18;
    margin: 5,10;
    color: rgb(224, 121, 140);
}
.search-bar {
  background-color: rgb(252, 231, 234);
  color: rgb(224, 121, 140);
  font-size: 16;
  height: 40;
  margin: 10;
  padding: 5;
}

.product-item {
    padding: 10;
    border-bottom-width: 1;
    border-color: #ccc;
}
.product-name {
    font-size: 18;
    font-weight: bold;
    margin-bottom: 5;
    color: rgb(224, 121, 140);
}

.product-price {
    font-size: 16;
    margin-bottom: 10;
}
.add-to-cart-btn {
    background-color: #333;
    width: 60%;
    color: #fff;
    height: 40;
    border-radius: 20;
    font-size: 16;
    vertical-align: middle;
    text-align: center;
}
.add-to-favorite-btn{
    background-color: rgb(224, 121, 140);
    width: 20%;
    color: #fff;
    height: 40;
    border-radius: 20;
    font-size: 16;
    vertical-align: middle;
    text-align: center;
}
</style>
