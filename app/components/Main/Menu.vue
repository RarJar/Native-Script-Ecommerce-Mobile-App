<template>
    <StackLayout class="bg-container">
            <StackLayout class="menuItem" @tap="aboutApp()">
                  <Image src="~/assets/icons/about.png" width="20"/>
                  <Label text="About Application" class="menu-item"></Label>
            </StackLayout>
            <StackLayout class="menuItem">
                  <Image src="~/assets/icons/bug.png" width="20"/>
                  <Label text="Feedback & Report Bugs" class="menu-item"></Label>
            </StackLayout>
            <StackLayout class="menuItem">
                  <Image src="~/assets/icons/privacy-policy.png" width="20"/>
                  <Label text="Privacy && Policy" class="menu-item"></Label>
            </StackLayout>
    </StackLayout>
</template>

<script>

export default {
    methods: {
      aboutApp() {
        alert({
              title: "E-commerce",
              message: "Version-1.0 && Copyright 2023",
              okButtonText: "Yes"
        });
      }
    }
};
</script>

<style scoped>
.bg-container {
  background-color: rgb(252, 239, 240);
  padding: 10px;
}
.menuItem{
  padding: 10;
  margin: 10,0;
  border-bottom-width: 1;
  border-bottom-color: pink;
  orientation: horizontal;
}

.menu-item{
  font-size: 15;
  margin-left: 10;
  color: rgb(217, 111, 130);
}
</style>
