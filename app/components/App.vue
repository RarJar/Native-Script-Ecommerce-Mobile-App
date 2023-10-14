<template>
  <Page>
    <MainActionBar />
    <TabView
      androidTabsPosition="bottom"
      tabTextColor="black"
      backgroundColor="red"
      selectedTabTextColor="#DE6288"
    >
      <TabViewItem title="Home" iconSource="~/assets/icons/home.png">
        <HomePage />
      </TabViewItem>

      <TabViewItem title="Shop" iconSource="~/assets/icons/shop.png">
        <ShopPage />
      </TabViewItem>

      <TabViewItem title="Cart" iconSource="~/assets/icons/cart.png">
        <CartPage />
      </TabViewItem>

      <TabViewItem title="Menu" iconSource="~/assets/icons/menu.png">
        <MenuPage />
      </TabViewItem>
    </TabView>
  </Page>
</template>

<script src="https://cdn.tailwindcss.com"></script>
<script lang="ts">
import Vue from "nativescript-vue";
import MainActionBar from "./ActionBar/MainActionBar.vue";

import HomePage from "./Main/Home.vue";
import ShopPage from "./Main/Shop.vue";
import CartPage from "./Main/Cart.vue";
import MenuPage from "./Main/Menu.vue";

import { getConnectionType } from "tns-core-modules/connectivity";

export default Vue.extend({
  components: {
    MainActionBar,
    HomePage,
    ShopPage,
    CartPage,
    MenuPage,
  },
  data() {
    return {
      connectionType: "",
    };
  },
  mounted() {
    this.checkConnectionType();
    alert(this.connectionType);
  },
  methods: {
    checkConnectionType() {
      const connectionType = getConnectionType();
      switch (connectionType) {
        case 0:
          this.connectionType = "No network connection";
          break;
        case 1:
          this.connectionType = "Cellular network connection";
          break;
        case 2:
          this.connectionType = "Wi-Fi network connection";
          break;
        case 3:
          this.connectionType = "Ethernet network connection";
          break;
        default:
          this.connectionType = "Unknown network connection";
          break;
      }
    },
  },
});
</script>

<style scoped lang="scss">
@import "@nativescript/theme/scss/variables/blue";

TabView {
  margin-bottom: -3;
  background-color: rebeccapurple;
}
</style>
