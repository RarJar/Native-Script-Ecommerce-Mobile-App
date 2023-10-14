<template>
    <Page class="page" actionBarHidden="true">
        <StackLayout class="form">
            <Image src="~/assets/images/loginSVG.png" class="loginImg" stretch="aspectFit" />
            <Label class="label" text="Email" />
            <TextField class="input" keyboardType="email" hint="Enter email address"/>

            <Label class="label" text="Password" />
            <TextField class="input" secure="true" hint="Enter your password"/>

            <Label class="forgot" text="Forgot your password?"/>

            <Button class="loginBtn" text="Login" @tap="onLoginButtonTap" />

            <StackLayout orientation="horizontal" verticalAlignment="center" horizontalAlignment="center">
                <Label class="haveAccount" text="Don't have an account?" />
                <Label class="toSignup" text="Sign Up" @tap="toSignUpPage"/>
            </StackLayout>
        </StackLayout>
    </Page>
</template>

<script>
import SignUpPage from "./Signup.vue";
import ProfilePage from "../Account/Profile.vue";

export default {
    methods: {
        onLoginButtonTap() {
            this.$navigateTo(ProfilePage);
        },

        toSignUpPage() {
            this.$navigateTo(SignUpPage);
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

.loginImg{
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

.forgot{
    color: rgb(252, 14, 14);
    font-size: 15;
    vertical-align: middle;
    text-align: center;
    margin-bottom: 5;
}

.loginBtn {
    font-size: 16;
    padding: 8;
    background-color: rgb(224, 121, 140);
    color: #ffffff;
    border-radius: 5;
    margin-bottom: 20;
}
.haveAccount{
    font-size: 16;
}

.toSignup{
    font-size: 17;
    color: rgb(214, 105, 125);
    margin-left: 4;
}
</style>
