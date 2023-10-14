<template>
    <Page>
        <ActionBar>
            <StackLayout orientation="horizontal" horizontalAlignment="left">
                <Image src="~/assets/icons/back.png" class="backIcon"/>
                <Label text="back" class="back"></Label>
            </StackLayout>
        </ActionBar>

        <ScrollView>
            <StackLayout class="bg-container">
                <Image src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQdghZ50ccDXYzNBNaNB4-mY-HpVFuMjvbw79v0Z9avqgXwmI8QtUV32FWNF0TTDrnZ6LY&usqp=CAU" class="product-image" />

                <Label text="Product name" class="product-name" />
                <Label text="$ 9.99" class="product-price" />
                <Label text="Description:" class="description-title" />
                <Label text="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed blandit massa vel mauris sollicitudin dignissim. Phasellus ultrices tellus eget ipsum ornare molestie scelerisque eros dignissim. Phasellus fringilla hendrerit lectus nec vehicula. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Nullam in aliquet odio." class="product-description"/>
                
                <StackLayout class="btn-container">
                    <Button text="Add to Cart" class="add-to-cart-button" />
                    <Image src="~/assets/icons/favorite.png" class="favoriteIcon"/>
                </StackLayout>

                <RelatedProductsView/>

            </StackLayout>
        </ScrollView>
    </Page>
</template>

<script>

import RelatedProductsView from "./RelatedProducts.vue";

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
    },
    components: {
        RelatedProductsView
    }
}
</script>

<style scoped>
.bg-container {
    background-color: rgb(252, 239, 240);
    padding: 10;
}

ActionBar{
    background-color: rgb(252, 231, 234);
}
.backIcon {
  width: 17;
  margin-right: 4;
}

.back{
    color: rgb(227, 123, 142);
    font-size: 15;
}

.product-image {
    width: 50%;
}
.product-name {
    font-size: 18;
    font-weight: 500;
    color: rgb(224, 121, 140);
}

.product-price {
    font-size: 16;
}

.description-title {
    font-size: 16;
}

.product-description {
    font-size: 14;
    line-height: 20;
}

.btn-container{
    orientation: horizontal;
}

.add-to-cart-button {
    background-color: #DE6288;
    width: 80%;
    color: #ffffff;
    border-radius: 10;
    font-size: 16;
    text-align: center;
}

.favoriteIcon{
    width: 35;
    height: 35;
    padding: 5;
    border-width: 1;
    border-color: #DE6288;
    border-radius: 50%;
}
</style>
