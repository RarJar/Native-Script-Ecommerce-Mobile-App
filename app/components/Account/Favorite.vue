<template>
    <Page>
        <ActionBar>
            <StackLayout orientation="horizontal" horizontalAlignment="left">
                <Image src="~/assets/icons/back.png" class="backIcon" @tap="$navigateBack"/>
                <Label text="back" class="back" @tap="$navigateBack"></Label>
            </StackLayout>
        </ActionBar>

        <StackLayout class="bg-container">
            <Label text="My Favorites" class="pageTitle"/>
            <ListView for="item in cartItems">
                <v-template>
                    <StackLayout orientation="horizontal">
                        <Image :src="item.image" stretch="aspectFit" width="15%" />

                        <StackLayout orientation="vertical" width="25%" verticalAlignment="center">
                            <Label :text="item.title" class="productName" />
                            <Label :text="'$' + item.price" />
                        </StackLayout>

                        <Button text="Add to cart" class="addToCartBtn"/>

                        <Button text="Remove" class="removeBtn" @tap="removeItem(item)" />
                    </StackLayout>
                </v-template>
            </ListView>
        </StackLayout>
    </Page>
</template>

<script>
export default {
    data() {
        return {
            cartItems: []
        }
    },
    methods: {
        removeItem(item) {
            const index = this.cartItems.findIndex((i) => i.id === item.id);
            if (index !== -1) {
                this.cartItems.splice(index, 1);
            }
        }
    },
    mounted() {
        fetch("https://fakestoreapi.com/products")
            .then(response => response.json())
            .then(result => {
                this.cartItems = result;
            });
    }
}
</script>

<style scoped>
.bg-container{
    background-color: rgb(252, 243, 244);
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

.pageTitle {
    font-weight: bold;
    font-size: 18;
    margin: 5, 10;
    color: rgb(224, 121, 140);
}
.productName {
    font-size: 16;
    font-weight: bold;
    color: rgb(224, 121, 140);
}
.addToCartBtn {
    background-color: rgb(224, 121, 140);
    color: #fff;
    width: 25%;
    height: 27;
    border-radius: 20;
    font-size: 15;
    vertical-align: middle;
    text-align: center;
}

.removeBtn {
    background-color: red;
    color: #fff;
    width: 20%;
    height: 27;
    border-radius: 20;
    font-size: 15;
    vertical-align: middle;
    text-align: center;
}
</style>
