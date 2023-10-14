<template>
  <ActionBar>
    <StackLayout orientation="horizontal">
      <Image src="~/assets/icons/shopLogo.png" width="40" />
      <Label text="E-Commerce" class="appTitle" />
      <Image
        src="~/assets/icons/favorite.png"
        class="favoriteIcon"
        @tap="toFavoritePage"
      />
      <Image src="~/assets/icons/user.png" width="27" @tap="toProfilePage" />
    </StackLayout>
  </ActionBar>
</template>

<script>
import FavoritePage from "../Account/Favorite.vue";
import LoginPage from "../Auth/Login.vue";

export default {
  methods: {
    toFavoritePage() {
      this.$navigateTo(FavoritePage);
    },
    toProfilePage() {
      this.$navigateTo(LoginPage);
    },
  },
};
</script>

<style scoped>
ActionBar {
  background-color: rgb(252, 231, 234);
}
.appTitle {
  width: 72%;
  font-size: 19;
  font-weight: 600;
  color: rgb(224, 121, 140);
}

.favoriteIcon {
  width: 27;
  margin-right: 6;
}
</style>
