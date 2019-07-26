<template>
  <Page>
    <ActionBar>
      <GridLayout width="100%" columns="auto, *">
        <!-- <Label text="Back " @tap="$navigateBack" col="0" /> -->
        <Label class="title" text="Home" col="1" />
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
        <ScrollView orientation="vertical" row="0">
            <StackLayout>
                <GridLayout rows="250, *,*" class="content">
                <WebView src="https://www.youtube.com/embed/rGh3GcwrtEQ" row="0" />
                <Label class="title" text="बिदेश जाँदै हुनुहुन्छ भने एउटा सम्पूर्ण प्याकेज । Baidesik Rojgar App Review" row="1" textWrap="true"/>
                <Label class="body" textWrap="true" text="हामी बिदेशमा काम गर्न जानकोलागी बिशेष गरेर दुई तरीका अनपाउन सक्छौँ 
 1- ब्याक्तिगत श्रम स्विकृती 
 2- म्यानपावर बाट श्रम लिएर 

यो भिडियोमा हामीले म्यानपावरबाट श्रम लिएर कसरी बिदेश जान सकीन्छ भनेर सेयर गरेका छौँ । बैदेशिक रोजगारीलाई धेरैले ठगी खाने ठाउँ बनाईरहेको बेलामा हामीले कुन जब पोस्ट साँचो हो कुन झुट हो भन्ने बिषयमा जान्नु जरुरी छ । हामीले यो भिडियोमा यि सबैकुरालाई अनलाईनमा कसरी चेक गर्न सकीन्छ भनेर पनि सेयर गरेका छौँ । लगायत धेरै कुराहरू छन् जसले तपाईँलाई धेरै हेल्प गर्नेछ । " row="2"/>
                </GridLayout>

                <GridLayout rows="250, *,*" class="content" @tap="openLink('https://foreignjob.dofe.gov.np/')">
                <Image src="~/assets/images/foreign_job_search.png"/>
                <Label class="title" text="यदी यहाँहरूले बैदेशीक रोजगारमा जानको लागी बिदेशमा जागिर खोजिरहनु भएको छ भने यो लिङ्कमा गएर आफ्नो  क्षमता अनुसारको जागीर खोज्न सक्नुहुन्छ । 
https://foreignjob.dofe.gov.np/" row="1" textWrap="true"/>
                </GridLayout>
            </StackLayout>
        </ScrollView>
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
import News from './News'
import Forum from './Forum'

export default {
  props: ["country", "option"],

  data() {
    return {
      selectedIndex: 0
    };
  },

  methods: {
    onSelectedIndexChange(index){
      this.selectedIndex = index.object.selectedIndex;
      switch(this.selectedIndex){
        case 0:
          break;
        case 1:
          this.$navigateTo(News);
          break;  
        case 2:
          this.$navigateTo(Forum);
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
    padding: 5;
    padding-bottom: 2;
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

