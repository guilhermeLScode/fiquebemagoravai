<template>
    <Page>
        <ActionBar title="Welcome to NativeScript-Vue!" android:flat="true"/>
        <TabView android:tabBackgroundColor="#53ba82"
                 android:tabTextColor="#c4ffdf"
                 android:selectedTabTextColor="#ffffff"
                 androidSelectedTabHighlightColor="#ffffff">
            <TabViewItem title="Tab 1">
                <GridLayout columns="*" rows="*">
           
                </GridLayout>
            </TabViewItem>
            <TabViewItem title="Tab 2">
                <GridLayout columns="*" rows="*">
                    <Label class="message" text="Tab 2 Content" col="0" row="0"/>
                </GridLayout>
            </TabViewItem>
            <TabViewItem title="Tab 3">
                <GridLayout columns="*" rows="*">
                    <Label class="message" text="Tab 3 Content" col="0" row="0"/>
                </GridLayout>
            </TabViewItem>
        </TabView>
    </Page>
</template>

<script>

  export default {
    name: "App",
    data() {
      return {
        latitude: '-29.8587727',
        longitude: '-51.1599591,17'
      }
    }, ,
       methods: {
            onMapReady(args) {
                var geolocation = require("nativescript-geolocation");
                geolocation.isEnabled().then(function (isEnabled) {
                    if (!isEnabled) {
                        geolocation.enableLocationRequest().then(function () {
                            
                        }, function (e) {
                            console.log("Error: " + (e.message || e));
                        });
                    } else {
                        let location = geolocation.getCurrentLocation({desiredAccuracy: 3, updateDistance: 10, maximumAge: 20000, timeout: 20000})
                            .then(function(resp) {

                            console.log("location");

                                this.latitude = resp.latitude;
                                this.longitude = resp.longitude;
                                // args.map.addMarkers([
                                //     {
                                //         lat: resp.latitude,
                                //         lng: resp.longitude,
                                //         title: "Tracy, CA",
                                //         subtitle: "Home of The Polyglot Developer!",
                                //         onCalloutTap: () => {
                                //             utils.openUrl("https://www.thepolyglotdeveloper.com");
                                //         }
                                //     }
                                // ]);
                            })
                    }
                }, function (e) {
                    console.log("Error: " + (e.message || e));
                });
            }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>
