<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="auto, *">
        <Label text="MENU" @tap="$refs.drawer.nativeView.showDrawer()" col="0" />
        <Label class="title" text="Welcome to NativeScript-Vue!" col="1" />
      </GridLayout>
    </ActionBar>

    <RadSideDrawer ref="drawer">
      <StackLayout ~drawerContent backgroundColor="#ffffff">
        <Label class="drawer-header" text="Drawer" />

        <Label class="drawer-item" text="Item 1" />
        <Label class="drawer-item" text="Item 2" />
        <Label class="drawer-item" text="Item 3" />
      </StackLayout>

      <GridLayout ~mainContent columns="*, *" rows="*,*,*" id="countries">
        <StackLayout row="0" col="0" @tap="toCountry('यूएई')">
          <Image src="~/assets/images/UAE.png" stretch="none" />
          <Label text="यूएई (दुबाई)" />
        </StackLayout>

        <StackLayout row="0" col="1" @tap="toCountry('मलेसिया')">
          <Image src="~/assets/images/malaysia.png" stretch="none" />
          <Label text="मलेसिया" />
        </StackLayout>

        <StackLayout row="1" col="0" @tap="toCountry('कतार')">
          <Image src="~/assets/images/qatar.png" stretch="none" />
          <Label text="कतार" />
        </StackLayout>

        <StackLayout row="1" col="1" @tap="toCountry('साउदी अरेबिया')">
          <Image src="~/assets/images/saudi.png" stretch="aspectFit" />
          <Label text="साउदी अरेबिया" />
        </StackLayout>

        <StackLayout row="2" col="0" @tap="toCountry('कुवेत')">
          <Image src="~/assets/images/kuwait.png" stretch="none" />
          <Label text="कुवेत" />
        </StackLayout>

        <StackLayout row="2" col="1" @tap="toCountry('ओमन')">
          <Image src="~/assets/images/oman.png" stretch="none" />
          <Label text="ओमन" />
        </StackLayout>
      </GridLayout>
    </RadSideDrawer>
  </Page>
</template>

<script >
import Country from "./Country.vue";

export default {
  data() {
    return {};
  },

  methods: {
    toCountry(country) {
      console.log(country);
      this.$navigateTo(Country, {
        props: {
          country: country
        }
      });
    }
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}

#countries StackLayout {
  padding: 15;
  margin: 5;
  border-width: 1;
  border-color: #3e3e3e80;
  border-radius: 0;
  android-elevation: 2;
}

label {
  font-size: 14;
  font-weight: bold;
  padding-top: 5;
  text-align: center;
}

.title {
  text-align: left;
  padding-left: 16;
}

.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}

.drawer-header {
  padding: 50 16 16 16;
  margin-bottom: 16;
  background-color: #53ba82;
  color: #ffffff;
  font-size: 24;
}

.drawer-item {
  padding: 8 16;
  color: #333333;
  font-size: 16;
}
</style>
