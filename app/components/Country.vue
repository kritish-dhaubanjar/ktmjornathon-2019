<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="auto, *">
        <!-- <Label text="Back " @tap="$navigateBack" col="0" /> -->
        <Label class="title" :text="'Welcome to ' + country " col="1" />
      </GridLayout>
    </ActionBar>

    <RadSideDrawer ref="drawer">
      <StackLayout ~drawerContent backgroundColor="#ffffff">
        <Label class="drawer-header" text="Drawer" />

        <Label class="drawer-item" text="Item 1" />
        <Label class="drawer-item" text="Item 2" />
        <Label class="drawer-item" text="Item 3" />
      </StackLayout>

      <GridLayout ~mainContent columns="*" rows="80,*" id="countries">
        <Label text="Please select an Option" class="pageTitle" row="0" />
        <ListView for="item in options" @itemTap="onItemTap" row="1">
          <v-template class="options">
            <Label :text="item.option" class="options" />
          </v-template>
        </ListView>
      </GridLayout>
    </RadSideDrawer>
  </Page>
</template>

<script>
import Option1 from "./Option1";
import Option2 from "./Option2";
import Option3 from "./Option3";
export default {
  props: ["country"],

  data() {
    return {
      options: [
        {
          id: 1,
          option:
            "तपाईँ अहिले नेपालमा हुनुहुन्छ " + this.country + "जान चहानुहुन्छ"
        },
        {
          id: 2,
          option: "तपाईँ अहिले " + this.country + "मै हुनुहुन्छ"
        },
        {
          id: 3,
          option: "एक आपसमा कुरा गर्नोस् "
        }
      ]
    };
  },

  methods: {
    onItemTap(event) {
        switch(event.item.id){
            case 1 :
            {
                this.$navigateTo(Option1, {
                    props: {
                    country: this.country,
                    option: event.item
                    }
                });
            }
            break;

            case 2 :
            {
                this.$navigateTo(Option2, {
                    props: {
                    country: this.country,
                    option: event.item
                    }
                });
            }
            break;

            case 3 :
            {
                this.$navigateTo(Option3, {
                    props: {
                    country: this.country,
                    option: event.item
                    }
                });
            }
            break;


            

        }
    }
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

