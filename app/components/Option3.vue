<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="auto, *">
        <!-- <Label text="Back " @tap="$navigateBack" col="0" /> -->
        <Label class="title" :text="this.option.option" col="1" />
      </GridLayout>
    </ActionBar>

    <RadSideDrawer ref="drawer">
      <StackLayout ~drawerContent backgroundColor="#ffffff">
        <Label class="drawer-header" text="Drawer" />

        <Label class="drawer-item" text="Item 1" />
        <Label class="drawer-item" text="Item 2" />
        <Label class="drawer-item" text="Item 3" />
      </StackLayout>

      <GridLayout id="countries" ~mainContent>
        <ScrollView orientation="vertical">
            <StackLayout>
                <GridLayout rows="250, *,*" class="content">
                <WebView src="https://www.youtube.com/embed/rGh3GcwrtEQ" row="0" />
                <Label class="title" text="बिदेश जाँदै हुनुहुन्छ भने एउटा सम्पूर्ण प्याकेज । Baidesik Rojgar App Review" row="1"/>
                <Label class="body" text="Lorem" row="2"/>
                </GridLayout>
            </StackLayout>
        </ScrollView>
      </GridLayout>
    </RadSideDrawer>
  </Page>
</template>

<script>
export default {
  props: ["country", "option"],

  data() {
    return {
    };
  },

  methods: {
    onItemTap() {}
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}
.content{
    margin: 10;
}
Label{
    padding: 5;
    margin-top: 5;
    font-weight: bold;
    font-size: 20;
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

