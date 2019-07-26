<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="*">
        <Label class="title" text="Q&A" col="0" />
      </GridLayout>
    </ActionBar>

    <RadSideDrawer ref="drawer">
      <StackLayout ~drawerContent backgroundColor="#ffffff">
        <Label class="drawer-header" text="Drawer" />

        <Label class="drawer-item" text="Item 1" />
        <Label class="drawer-item" text="Item 2" />
        <Label class="drawer-item" text="Item 3" />
      </StackLayout>

      <GridLayout ~mainContent rows="56,*,56">
        <StackLayout>
        <Label textWrap="true" :text="item.title" row="0">

        <ListView for="answer in item.answers" @itemTap="onItemTap" row="1">
            <v-template>
                <Label textWrap="true" :text="answer"/>
            </v-template>
        </ListView>

        <SegmentedBar row="2" :selectedIndex="selectedIndex" @selectedIndexChange="onSelectedIndexChange">
          <SegmentedBarItem title="Home" />
          <SegmentedBarItem title="News" />
          <SegmentedBarItem title="Forum" />
        </SegmentedBar>
        </StackLayout>
      </GridLayout>
    </RadSideDrawer>
  </Page>
</template>

<script>
import MyWebview from './MyWebview'
import Option1 from './Option1'
import News from './News'
export default {
    props: ["item"],

    created(){
        console.log(this.item.answers);
    },

  data() {
    return {
      selectedIndex: 2,
    };
  },


  methods: {
    onItemTap(event){},
    onSelectedIndexChange(index){
      this.selectedIndex = index.object.selectedIndex;
      switch(this.selectedIndex){
        case 0:
          this.$navigateTo(Option1);
          break;
        case 1:
          this.$navigateTo(News);
          break;  
        case 2:
          break;  
      }
    },
    openLink(src) {
      // console.log(src);
      this.$navigateTo(MyWebview, {
        props:{
          link: src
        }
      })
    }
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
    border-width: 1;
    border-color: #3e3e3e80;
    border-radius: 0;
    android-elevation: 2;
}

.body{
  font-size: 16;
  font-weight: normal;
  margin-top: 0;
  padding-bottom: 5;
}
Label{
    padding-top: 10;
    padding-bottom: 10;
    padding-left: 5;
    padding-right: 5;
    font-size: 17;
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

