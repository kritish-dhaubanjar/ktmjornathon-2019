<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="auto, *">
        <!-- <Label text="Back " @tap="$navigateBack" col="0" /> -->
        <Label class="title" text="Forum" col="1" />
      </GridLayout>
    </ActionBar>

    <RadSideDrawer ref="drawer">
      <StackLayout ~drawerContent backgroundColor="#ffffff">
        <Label class="drawer-header" text="Drawer" />

        <Label class="drawer-item" text="Item 1" />
        <Label class="drawer-item" text="Item 2" />
        <Label class="drawer-item" text="Item 3" />
      </StackLayout>

      <GridLayout id="countries" ~mainContent rows="*,56">

          <ListView for="item in listOfItems" @itemTap="onItemTap">
            <v-template>
                <StackLayout>
                <GridLayout columns="*, 50">
                    <Label textWrap="true" :text="item.title" col="0"/>
                    <StackLayout col="1">
                    <Image src="~/assets/images/baseline_thumb_up_black_36dp.png" stretch="none" @tap="++item.count"/>
                    <Label :text="item.count"/> 
                    </StackLayout>
                </GridLayout>
                </StackLayout>
            </v-template>
        </ListView>

        <SegmentedBar row="1" :selectedIndex="selectedIndex" @selectedIndexChange="onSelectedIndexChange">
          <SegmentedBarItem title="Home" />
          <SegmentedBarItem title="News" />
          <SegmentedBarItem title="Forum" />
        </SegmentedBar>
      </GridLayout>
    </RadSideDrawer>
  </Page>
</template>

<script>
import MyWebview from './MyWebview'
import Option1 from './Option1'
import News from './News'
import Answer from './Answer'
export default {

  data() {
    return {
      selectedIndex: 2,
      listOfItems: [
          {
              id: 1,
              title: "Dubai ra Abu Dhabi tollgate ko salik striker yautai huncha ki farak k yasko jaankar cha ?",
              count: 102,
              answers: [
                  "Lorem",
                  "Ipsum",
                  "Dolor",
                  "Sit",
                  "Amet"
              ]
          },
          {
              id: 2,
              title: "6month complete vako limited contract. Ahile resign Garda company le 6000pay gar vandai xa. Taseel ma bhujda 45days ko salary matra pay garnu parxa vanxa.ban lagla ki vanne dar chha k Garda hola?",
              count: 80,
              answers: [
                  "Lorem",
                  "Ipsum",
                  "Dolor",
                  "Sit",
                  "Amet"
              ]
          },
          {
              id: 3,
              title: "Rp sir hajur sanga inbox ma kura garna parni thyo k kasto time xa hajursanga ??",
              count: 20,
              answers: [
                  "Lorem",
                  "Ipsum",
                  "Dolor",
                  "Sit",
                  "Amet"
              ]
          }
      ]
    };
  },


  methods: {
    onItemTap(event){
        this.$navigateTo(Answer,{
            props: {
                item: event.item
            }
        })
    },
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

