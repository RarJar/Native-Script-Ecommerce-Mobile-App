<template>
    <Page class="page" actionBarHidden="true">
        <ActionBar>
            <StackLayout orientation="horizontal">
                <Image src="~/assets/icons/shopLogo.png" width="40" />
                <Label text="E-Commerce" class="appTitle" />
            </StackLayout>
        </ActionBar>

        <StackLayout class="form">
            <Image src="~/assets/images/loginSVG.png" class="loginImg" stretch="aspectFit" />

            <Label class="label" text="Name" />
            <TextField class="input" v-model="email" keyboardType="email" hint="Enter your name" />

            <Label class="label" text="Email" />
            <TextField class="input" v-model="email" keyboardType="email" hint="Enter email address" />

            <Label class="label" text="Password" />
            <TextField class="input" v-model="password" secure="true" hint="Enter your password" />

            <Label class="label" text="Confirm password" />
            <TextField class="input" v-model="password" secure="true" hint="Confirm your password" />

            <Button class="signupBtn" text="Sign Up"/>

            <StackLayout orientation="horizontal" verticalAlignment="center" horizontalAlignment="center">
                <Label class="haveAccount" text="Already have an account?" />
                <Label class="toLogin" text="Login now" @tap="toLoginPage"/>
            </StackLayout>
        </StackLayout>
    </Page>
</template>

<script>
import LoginPage from "./Login.vue";

export default {
    methods: {
        toLoginPage() {
            this.$navigateTo(LoginPage);
        }
    }
};
</script>

<style scoped>
.page {
    background-image: url("~/assets/images/registerBackground.png");
    background-size: cover;
    background-position: center;
}

ActionBar{
    background: rgb(236, 232, 232);
    height: 0;
}
.appTitle{
      width: 100%;
      font-size: 19;
      font-weight: 600;
      color: rgb(224, 121, 140);
}

.form {
    margin: 15;
    vertical-align: middle;
}

.loginImg {
    width: 270;
    margin-bottom: 15;
}

.label {
    font-size: 16;
    margin: 0, 0, 5, 20;
}

.input {
    font-size: 15;
    padding: 10;
    border-width: 1;
    border-color: rgb(248, 171, 183);
    margin-bottom: 20;
    border-radius: 5;
    placeholder-color: gray;
}

.signupBtn {
    font-size: 16;
    padding: 8;
    background-color: rgb(224, 121, 140);
    color: #ffffff;
    border-radius: 5;
    margin-bottom: 20;
}

.haveAccount {
    font-size: 16;
}

.toLogin {
    font-size: 17;
    color: rgb(214, 105, 125);
    margin-left: 4;
}
</style>
