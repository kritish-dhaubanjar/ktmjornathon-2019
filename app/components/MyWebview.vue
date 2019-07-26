<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="auto, *">
        <Label class="title" :text="link" col="1" />
      </GridLayout>
    </ActionBar>

    <RadSideDrawer ref="drawer">
      <StackLayout ~drawerContent backgroundColor="#ffffff">
        <Label class="drawer-header" text="Drawer" />

        <Label class="drawer-item" text="Item 1" />
        <Label class="drawer-item" text="Item 2" />
        <Label class="drawer-item" text="Item 3" />
      </StackLayout>

      <GridLayout ~mainContent columns="*" rows="*">
        <WebView :src="link" row="0" col="0"/>
      </GridLayout>  
    </RadSideDrawer>
  </Page>
</template>

<script>
export default {
  props: ["link"],

  created(){
      console.log(this.link);
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}
.pageTitle {
  text-align: center;
  padding: 15;
  font-size: 20;
  font-weight: bold;
}
.options {
  padding: 15;
  font-size: 20;
  font-weight: bold;
}
</style>

