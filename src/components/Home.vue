<template>
  <div>
    <v-carousel cycle="true" interval="4000">
      <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="item.src"
        transition="fade-transition"
      ></v-carousel-item>
    </v-carousel>
    
      </div>
    </v-img>
  </div>
</template>
<script>
import { bus } from "../main";
export default {
  data() {
    return {
      loaded: false,
      paidFor: false,
      product: {
        price: 777.77,
        description: "leg lamp from that one movie",
        img: "./assets/lamp.jpg"
      },
      rateCard: 0,
      screensize: 0,
      tab: null,
      rateCards: [
        { src: require("../assets/wifinity/Ratecardbasic.svg"), plan: "basic" },
        { src: require("../assets/wifinity/Ratecardplus.svg"), plan: "plus" },
        {
          src: require("../assets/wifinity/Ratecardpremium.svg"),
          plan: "premium"
        },
        { src: require("../assets/wifinity/Ratecardvip.svg"), plan: "vip" }
      ],

      items: [
        {
          src: require("../assets/wifinity/wifinitytv.jpg")
        },
        {
          src: require("../assets/wifinity/Family-Watching.jpg")
        },
        {
          src: require("../assets/wifinity/family-watching.jpg")
        },
        {
          src: require("../assets/wifinity/multisport.webp")
        }
      ],

      tabsContent: [
        {
          tab: 0,
          item: "MultiDevice",
          icon: "phonelink",
          content:
            "WifinityTv is available on mobilePhones, Tablets, Web, SmartTv's, AndroidBox and Other technologies.We have saved you the hussle, so that any time you feel like watching your favourite programme, just grab your nearest device and you are Good to go!.Download the WifinityTv app and get streaming."
        },
        {
          tab: 1,
          item: "SplitScreen",
          icon: "vertical_split",
          content:
            "SplitView lets you watch up to four videos at once, all on the same screen, on selected devices.With this feature you can follow up on multiple programmes airing at the same time. We know you love multi-tasking and that feature is right here for you."
        },
        {
          tab: 2,
          item: "HighDefination",
          icon: "hd",
          content:
            "Get up close and personal with your favourite Tv programmes. As good as being there live.Every glorious moment delivered in the clearest detail. All content streamed in WifinityTv is available in a HD stream, provided you have a reliable internet connection."
        },

        {
          tab: 3,
          item: "GlobalAccess",
          icon: "public",
          content:
            "WifinityTv lets you catch up with your favourite programmes from any location in the world. So next time you are on travel save yourself the worry about missing the next episode of your favourite show because we have your back. Get your device , SignIn and there you go."
        }
      ],
      other_devices: [
        "M3u",
        "Zorro",
        "Revolution|Sunplus",
        "Spark",
        "Ariva",
        "Octagon",
        "StarLive",
        "Enigma",
        "MediaStar",
        "DreamBox",
        "GigaBlue",
        "Geant",
        "Fortec999"
      ],
      tab_no: 0
    };
  },
  created() {
    window.addEventListener("resize", this.myEventHandler);
  },

  destroyed() {
    window.removeEventListener("resize", this.myEventHandler);
  },

  methods: {
    checkout(plan) {
      bus.$emit("selected_plan", plan);
    },
    myEventHandler(e) {
      console.log(e);
      const width = window.innerWidth;
      if (width < 768) {
        this.cardWidth = 150;
      } else this.cardWidth = 250;
    },
    updateTabContent(e) {
      console.log("user clicked tab " + e);
      this.active_link = true;
      var addElement;
      var removeElement;
      switch (e) {
        case 0:
          this.tab_no = 0;
          addElement = document.getElementById("tab1");
          addElement.classList.add("active_link1");
          removeElement = document
            .getElementById("tab2")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab3")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab4")
            .classList.remove("active_link1");
          console.log("Clicked the following" + removeElement);
          break;
        case 1:
          this.tab_no = 1;
          addElement = document.getElementById("tab2");
          addElement.classList.add("active_link1");
          removeElement = document
            .getElementById("tab1")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab3")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab4")
            .classList.remove("active_link1");
          console.log("Clicked the following" + removeElement);
          break;
        case 2:
          this.tab_no = 2;
          addElement = document.getElementById("tab3");
          addElement.classList.add("active_link1");
          removeElement = document
            .getElementById("tab1")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab2")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab4")
            .classList.remove("active_link1");
          console.log("Clicked the following" + removeElement);
          break;
        case 3:
          this.tab_no = 3;
          addElement = document.getElementById("tab4");
          addElement.classList.add("active_link1");
          removeElement = document
            .getElementById("tab1")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab3")
            .classList.remove("active_link1");
          removeElement = document
            .getElementById("tab2")
            .classList.remove("active_link1");
          console.log("Clicked the following" + removeElement);
          break;
        default:
          this.tab_no = 0;
      }
    }
  }
};
</script>

<style lang="stylus" scoped>
$footer = #0A0A10;
$footer1 = #1A518E;
$feature = #1D0C42;
$feature1 = #0D0F19;
$active_link = #FFDC39;
$active_link_background = #0F0C2E;

.wifinity-desc {
  position: relative;
  top: 20px;
  line-height: 25px;
  font-family: Raleway;
  font-type: normal;
  font-weight: normal;
  font-size: 18px;
  color: white;
}

.wifinity-card, .overlay {
  background-color: rgba(8, 45, 114, 0.5);
  height: 100%;
}

.features-label {
  position: relative;
  width: 100%;
  height: 100px;
  background: $feature;
  color: white;
  font-size: 40px;

  @media screen and (max-width: 576px) {
    font-size: 25px;
    height: 70px;
  }
}

.features {
  position: relative;
  width: 100%;
  height: 200px;
  text-decoration: none;
}

.tab-content {
  color: white;
  font-weight: 600;
  height: 300px;
  position: relative;
}

.content-container {
  height: 150px;
  margin-left: 180px;
  max-width: 820px;

  @media screen and (max-width: 1256px) {
    margin-left: 0;
    height: 40px;
  }
}

.tabs {
  height: 150px;
  width: 100%;
  position: relative;
  color: white;
  margin: 0px;
}

.tab-items {
  width: 100%;
  position: absolute;
  top: 20px;
  margin: 0;
}

.tabs li {
  list-style-type: none;
  display: inline;
  margin: 0 50px;

  @media screen and (max-width: 576px) {
    margin: 0 8px;
  }
}

.tab_buttn {
  padding: 20px;
  position: relative;
  display: block;
  width: 130px;
  text-align: center;

  @media screen and (max-width: 576px) {
    width: 90px;
  }

  &:hover::after {
    content: '';
    position: absolute;
    left: 25%;
    right: 25%;
    bottom: 0;
    border: 2px solid $active_link;
    border-radius: 2px;
  }
}

.btn-txt {
  margin-top: 15px;

  @media screen and (max-width: 576px) {
    font-size: 10px;
    margin-top: 5px;
  }
}

.active_link1 {
  color: white;
  background: $active_link_background;
  border-radius: 4px;
}

.active_link1::after {
  content: '';
  position: absolute;
  left: 25%;
  right: 25%;
  bottom: 0;
  border: 2px solid $active_link;
  border-radius: 2px;
}

.devices {
  color: white;
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 80px;
  background: rgba(15, 12, 46, 0.56);

  @media screen and (max-width: 1260px) {
    overflow-x: scroll;
    scrollbar-color: white;
  }

  @media screen and (max-width: 576px) {
    height: 50px;
  }
}

.devices li {
  list-style-type: none;
  display: inline;
  margin: 10px;
  width: 30px;
}

.devices-list {
  width: 100%;
  padding: 10px;
  margin: 0;
}

.devices-list-label {
  color: white;
  position: absolute;
  top: 160px;
  width: 100%;
  height: 80px;
  font-size: 40px;

  @media screen and (max-width: 576px) {
    font-size: 25px;
    top: 210px;
  }
}

.price-cards-container {
  width: 100%;
  height: 400px;
  background: #EEEEF1;
  position: relative;

  @media screen and (max-width: 576px) {
    height: 400px;
  }
}

.mobile-price-card {
  position: absolute;
  left: 50px;
  top: 20px;
}
</style>