<template>
    <StackLayout class="bg-container">
        <Label text="My Cart" class="pageTitle"/>
            <WrapLayout orientation="vertical" class="checkoutContainer">
                    <StackLayout orientation="horizontal">
                        <Label text="Sub total" class="totalTitle"/>
                        <Label text="$ 100" class="fee"/>
                    </StackLayout>
                    <StackLayout orientation="horizontal">
                        <Label text="Delivery Fee" class="totalTitle"/>
                        <Label text="$ 50" class="fee"/>
                    </StackLayout>
                    <StackLayout orientation="horizontal">
                        <Label text="Total" class="totalTitle"/>
                        <Label text="$ 150" class="fee"/>
                    </StackLayout>
                    <Button text="Checkout & Order" class="checkoutBtn"/>
            </WrapLayout>
            <ListView for="item in cartItems">
                        <v-template>
                            <StackLayout class="product-item" orientation="horizontal">
                                <Image :src="item.image" stretch="aspectFit" width="15%"/>

                                <StackLayout orientation="vertical" width="30%" verticalAlignment="center">
                                    <Label :text="item.title" class="cartName"/>
                                    <Label :text="'$' + item.price"/>
                                </StackLayout>

                                <StackLayout orientation="horizontal" width="25%" verticalAlignment="center" horizontalAlignment="center">
                                    <Label text="-" class="qtyEditBtn"/>
                                    <Label text="10" class="cartQuantity"/>
                                    <Label text="+" class="qtyEditBtn"/>
                                </StackLayout>

                            <Button text="Remove" width="20%" class="cartRemoveBtn" @tap="removeItem(item)"/>
                        </StackLayout>
                    </v-template>
        </ListView>
    </StackLayout>
</template>

<script>
export default {
    data () {
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
    mounted () {
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
    background-color: rgb(252, 239, 240);
}
.pageTitle{
    font-weight: bold;
    font-size: 18;
    margin: 5,10;
    color: rgb(224, 121, 140);
}
.cartName{
    font-size: 16;
    font-weight: bold;
    color: rgb(224, 121, 140);
}

.qtyEditBtn{
    background-color: rgb(97, 92, 92);
    color: #fff;
    width: 30;
    height: 30;
    border-radius: 100%;
    font-size: 15;
    vertical-align: middle;
    text-align: center;
}
.cartQuantity{
    font-size: 17;
}
.cartRemoveBtn{
    background-color: rgb(229, 33, 33);
    color: #fff;
    height: 27;
    border-radius: 20;
    font-size: 15;
    vertical-align: middle;
    text-align: center;
}

/* Checkout */
.checkoutContainer{
    height: 20%;
    padding: 5,5,0,5;
    border-bottom-width: 1;
    border-bottom-color: pink;
}
.totalTitle{
    width: 60%;
    font-size: 16;
    font-weight: bold;
    margin-left: 10;
}

.fee{
    width: 30%;
    font-size: 16;
    vertical-align: middle;
    text-align: center;
}

.checkoutBtn{
    background-color: rgb(224, 121, 140);
    color: #fff;
    width: 90%;
    height: 30;
    border-radius: 20;
    font-size: 16;
    text-align: center;
}
</style>
