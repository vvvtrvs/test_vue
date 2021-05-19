<template>
  <v-container fluid class="pa-0 ma-0">
    <v-row no-gutters class="cyan">
      <hero-section class="px-12 py-8 text-center text-sm-left">
        <template v-slot:heading>
          <h1 class="">GagaKing讓你<br />無需佣金租買靚盤！</h1>
        </template>

        <template v-slot:img>
          <v-responsive aspect-ratio="1">
            <v-sheet class="white fill-height text-center align-center">
            </v-sheet>
          </v-responsive>
        </template>

        <template v-slot:body>
          <h5 class="mb-2">GagaKing讓你無需佣金租買靚盤！</h5>
          <v-btn
            @click.stop=""
            class="my-1 px-5"
            elevation="0"
            color="primary"
            rounded
            >放盤
            <v-icon>mdi-arrow-right</v-icon>
          </v-btn>
          <br />
          <v-btn
            @click.stop=""
            class="my-1 px-5"
            outlined
            color="primary"
            rounded
          >
            搵樓
            <v-icon>mdi-arrow-right</v-icon>
          </v-btn>
        </template>
      </hero-section>
    </v-row>

    <v-row
      no-gutters
      v-for="(section, i) in sections"
      :key="i"
      :class="section.background"
    >
      <hero-section
        :class="[
          'px-12',
          'py-8',
          'text-center',
          { 'text-sm-left': !!section.image }
        ]"
        reverse
        :wide="!!section.image"
      >
        <template v-slot:heading>
          <h1 class="">{{ section.heading }}</h1>
        </template>

        <template v-slot:img>
          <v-img
            class="fill-height"
            :src="section.image"
            aspect-ratio="1"
            contain
            v-if="!!section.image"
          >
          </v-img>
        </template>

        <template v-slot:body>
          <v-list dense flat disabled class="d-inline-block text-left">
            <v-list-item v-for="(item, i) in section.items" :key="i">
              <v-list-item-icon class="mr-3">
                <v-icon v-text="item.icon"></v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title v-text="item.text"></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
          <br />
          <v-btn
            @click.stop=""
            class="my-1 px-5"
            outlined
            color="primary"
            rounded
            v-if="section.action"
          >
            {{ section.action }}
            <v-icon>mdi-arrow-right</v-icon>
          </v-btn>
        </template>
      </hero-section>
    </v-row>
  </v-container>
</template>

<script>
import HeroSection from "~/components/HeroSection.vue";
export default {
  components: { HeroSection },
  computed: {
    xs() {
      return this.$vuetify.breakpoint.name == "xs";
    }
  },
  data() {
    return {
      sections: [
        {
          background: "light-grey",
          heading: "傾好價 點簽合約？",
          image: "section1.png",
          items: [
            {
              icon: "mdi-magnify",
              text: "免費合約下載 唔洗四圍搵"
            },
            {
              icon: "mdi-phone-outline",
              text: "精選律師樓 「佢幫到你」"
            },
            {
              icon: "mdi-magnify",
              text: "填寫租約 「佢幫到你」"
            }
          ],
          action: "下載免費合約"
        },
        {
          shade: false,
          heading: "傾好價 點簽合約？",
          image: "section2.png",
          items: [
            {
              icon: "mdi-magnify",
              text: "免費合約下載 唔洗四圍搵"
            },
            {
              icon: "mdi-phone-outline",
              text: "精選律師樓 「佢幫到你」"
            },
            {
              icon: "mdi-magnify",
              text: "填寫租約 「佢幫到你」"
            }
          ],
          action: "下載免費合約"
        },
        {
          background: "light-grey",
          heading: "傾好價 點簽合約？",
          image: "section3.png",
          items: [
            {
              icon: "mdi-magnify",
              text: "免費合約下載 唔洗四圍搵"
            },
            {
              icon: "mdi-phone-outline",
              text: "精選律師樓 「佢幫到你」"
            },
            {
              icon: "mdi-magnify",
              text: "填寫租約 「佢幫到你」"
            }
          ],
          action: "下載免費合約"
        },
        {
          background: "light-grey",
          heading: "傾好價 點簽合約？",
          image: "section4.png",
          items: [
            {
              icon: "mdi-magnify",
              text: "免費合約下載 唔洗四圍搵"
            },
            {
              icon: "mdi-phone-outline",
              text: "精選律師樓 「佢幫到你」"
            },
            {
              icon: "mdi-magnify",
              text: "填寫租約 「佢幫到你」"
            }
          ],
          action: "下載免費合約"
        },
        {
          background: "background2", // no idea what the color/pattern is called
          heading: "傾好價 點簽合約？",
          items: [
            {
              icon: "mdi-magnify",
              text: "免費合約下載 唔洗四圍搵"
            },
            {
              icon: "mdi-phone-outline",
              text: "精選律師樓 「佢幫到你」"
            },
            {
              icon: "mdi-magnify",
              text: "填寫租約 「佢幫到你」"
            }
          ]
        }
      ]
    };
  }
};
</script>

<style scoped>
h1 {
  letter-spacing: 0.1em;
}
.v-btn--outlined {
  background-color: white;
}
.v-list {
  background: none;
}
.light-grey {
  background-color: #f4f3f8;
}
.background2 {
  background-color: #d1f1ff;
}
</style>
