<template>
  <Page actionBarHidden="true">
    <StackLayout class="bg-container">
      <StackLayout class="header-container">
        <StackLayout class="backpage-container">
          <Image
            src="~/assets/icons/back.png"
            class="backIcon"
            @tap="$navigateBack"
          />
          <Label text="back" @tap="$navigateBack"></Label>
        </StackLayout>

        <Image
          src="https://dl.memuplay.com/new_market/img/com.vicman.newprofilepic.icon.2022-06-07-21-33-07.png"
          class="profile-image"
        />
        <Label text="John Doe" class="profile-name" />
        <Label text="+959 252250030" class="profile-phone" />
        <Label text="johndoe@gmail.com" class="profile-email" />
      </StackLayout>

      <StackLayout class="body-container">
        <StackLayout class="menuItem">
          <Image src="~/assets/icons/edit.png" width="20" />
          <Label text="Edit Profile" class="menu-item"></Label>
        </StackLayout>
        <StackLayout class="menuItem">
          <Image src="~/assets/icons/reload.png" width="20" />
          <Label text="Change Password" class="menu-item"></Label>
        </StackLayout>
        <StackLayout class="menuItem">
          <Image src="~/assets/icons/checkout.png" width="20" />
          <Label text="My Orders" class="menu-item"></Label>
        </StackLayout>
        <StackLayout class="menuItem" @tap="onLogout">
          <Image src="~/assets/icons/power-off.png" width="20" />
          <Label text="Logout" class="menu-item"></Label>
        </StackLayout>
      </StackLayout>
    </StackLayout>
  </Page>
</template>

<script>
import LoginPage from "../Auth/Login.vue";

export default {
  methods: {
    onBackPage() {},

    onLogout() {
      confirm({
        title: "Confirm Logout",
        message: "Are you sure you want to logout?",
        okButtonText: "Ok",
        cancelButtonText: "Cancel",
      }).then((result) => {
        if (result) {
          this.$navigateTo(LoginPage);
        }
      });
    },
  },
};
</script>

<style scoped>
.bg-container {
  align-items: center;
  background-color: rgb(252, 243, 244);
}

.header-container {
  border-radius: 0, 0, 30, 30;
  padding: 0, 0, 30, 0;
  text-align: center;
  background-image: url("~/assets/images/registerBackground.png");
}
.backpage-container {
  color: rgb(227, 123, 142);
  padding: 10;
  orientation: horizontal;
  font-size: 15;
}

.backpage-container .backIcon {
  width: 17;
  margin-right: 4;
}

.profile-image {
  width: 80;
  height: 80;
  border-radius: 50;
}

.profile-name {
  font-size: 18;
  font-weight: bold;
  margin: 5, 0;
  color: rgb(48, 47, 47);
}

.profile-email,
.profile-email {
  font-size: 16;
  color: rgb(57, 56, 56);
}

.body-container {
  padding: 10px;
}
.menuItem {
  padding: 20;
  border-bottom-width: 1;
  border-bottom-color: rgb(249, 212, 219);
  orientation: horizontal;
}

.menu-item {
  font-size: 15;
  margin-left: 10;
  color: rgb(217, 111, 130);
}
</style>
