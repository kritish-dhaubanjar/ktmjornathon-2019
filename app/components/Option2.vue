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

      <GridLayout id="countries" ~mainContent rows="*,56">
        <ScrollView orientation="vertical" row="0">
            <StackLayout>
                <GridLayout rows="250, *,*" class="content" @tap="openLink('https://eservices.mohre.gov.ae/enetwasal/employeeCredential.aspx')">
                <Image src="~/assets/images/salary.png" stretch="aspectFit"/>
                <Label class="title" textWrap="true" text="तपाईँ काम गरीरहेको कम्पनिले भनेजती स्यालरी दिएन भने यहाँहरूले केही ठाउँहरुमा कम्प्लेन गर्न सक्नुहुन्छ ।" row="1"/>
                <Label class="body" textWrap="true" text="-    पहिलो स्टेप भनेको तपाईँ काम गर्दै गरेको कम्पनिले लगातार २ महिनासम्म स्यालरी नदिएको खन्डमा यहाँले यो कम्ल्लेन गर्नु पर्छ र कम्पनिको अबस्था हेरेर आफ्नो म्यानेजर वा HR म्यानेजर सँग कुरा गरेर कहिले स्यालरी दिन्छ भन्ने कुरा फिक्स गर्नु पर्ने हुन्छ
-    यदी अझै पनि स्यालरी पाईएन भने तपाईँ जुन मेनपावरबाट जानु भएको हो त्यो मेन पावरमा कुरा गर्नोस् ।
-    त्यसलै कुनै रेस्पोन्स नदेखाएको खन्डमा नेपाल एम्बेसीलाई खबर गरेर एउटा निबेदन लेख्न सक्नुहुन्छ ।
-    नेपालमा भएको बैदेशीक रोजगार बिभागमा श्रम मन्रालयको कलसेन्टरमा म्यासेज या WhatsApp/Viber पनि गर्न सक्नुहुन्छ ।
-    Facebook:  https://www.facebook.com/molcallcenter/
-    Viber: +9779801800013
-    र यदी यि सबैकुराभन्दा यहाँलाई सजिलो हुने अर्को कुरा पनि हामी यहाँलाई बताउँछौँ ।
-    यहाँहरूले यूएईमा भएको गभर्नमेन्ट साईड MOHRE मा पनि यहाँहरूले आफूले स्यालरी नपाएको कुरा दर्ता गर्न सक्नुहुन्छ ।
-    https://eservices.mohre.gov.ae/enetwasal/employeeCredential.aspx" row="2"/>
                </GridLayout>

                <GridLayout rows="250, *,*" class="content">
                <WebView src="https://www.youtube.com/embed/wbWAIv-GuHI" row="0" />
                <Label class="title" textWrap="true" text="UAE मा हुँदा जागिर कसरी चेन्ज गर्ने ? " row="1"/>
                <Label class="body" textWrap="true" text="कहिलेकाहीँ हाम्रो क्षमताको कारणले गर्दा हामिले नयाँ नयाँ कम्पनिहरुमा नयाँ नयाँ जागिरको लागी अफरहरू पाउन पनि सक्छौँ । यस्तो अबस्था आएको खन्ड या कहिले काँहिँ हामीले अहिले काम गरीरहेको कम्पनिमा काम चेन्ज गरेर नयाँ काम खोजीरहेका हुन्छौँ यस्तो अवस्थामा हामिले कसरी गर्न सक्छौँ यो भोडियोमा हामीले सेयर गरेका छौँ । " row="2"/>
                </GridLayout>
            </StackLayout>
        </ScrollView>
        <SegmentedBar row="1" :selectedIndex="0">
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
export default {
  props: ["country", "option"],

  data() {
    return {
    };
  },

  methods: {
    onItemTap() {},

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
Label{
    padding: 5;
    margin-top: 5;
    font-weight: bold;
    font-size: 20;
}
.body{
  font-size: 16;
  font-weight: normal;
  margin-top: 0;
  padding-bottom: 5;
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

