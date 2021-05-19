<template>
  <v-app>
    <v-app-bar
      class="px-sm-10"
      color="white"
      fixed
      app
      elevation="1"
      extension-height="24px"
    >
      <template v-slot:default>
        <v-img
          :src="require('@/static/logo.png')"
          contain
          aspect-ratio="3"
          min-width="150"
          max-width="170"
        ></v-img>

        <v-spacer />

        <v-btn
          v-for="(link, i) in toolbarLinks"
          :key="i"
          :to="link.to"
          router
          exact
          rounded
          text
        >
          {{ link.title }}
        </v-btn>

        <v-spacer />

        <v-badge
          color="red"
          overlap
          :content="notifications"
          :value="notifications"
          offset-x="20"
          offset-y="20"
        >
          <v-btn icon @click.stop="">
            <v-icon>mdi-crown-outline</v-icon>
          </v-btn>
        </v-badge>
        <v-btn icon @click.stop="">
          <v-icon>mdi-account-outline</v-icon>
        </v-btn>
        <v-divider vertical inset />
        <v-btn text @click.stop="" class="text-capitalize">
          En
          <v-icon>mdi-menu-down</v-icon>
        </v-btn>
        <v-btn icon @click.stop="rightDrawer = !rightDrawer">
          <v-icon>mdi-menu</v-icon>
        </v-btn>
      </template>

      <template v-slot:extension>
        <v-container class="search-container pa-0">
          <v-row no-gutters>
            <v-col cols="12">
              <search-bar></search-bar>
            </v-col>
          </v-row>
        </v-container>
      </template>
    </v-app-bar>

    <v-main>
      <nuxt />
    </v-main>

    <v-navigation-drawer
      app
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item
          v-for="(link, i) in navLinks"
          :key="i"
          :to="link.to"
          router
          exact
        >
          <v-list-item-content>
            <v-list-item-title v-text="link.title"> </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer dark color="#04202c">
      <v-container>
        <v-row align="start" class="mt-4 mb-8">
          <v-col cols="3" sm="2">
            <v-img
              :src="require('@/static/logo-dark.png')"
              max-width="100"
            ></v-img>
          </v-col>
          <v-col
            cols="3"
            sm="auto"
            v-for="(column, i) in footerLinks"
            :key="i"
            class="text-center"
          >
            <template v-for="(link, j) in column">
              <v-btn :key="j" :to="link.to" text class="text-capitalize">
                {{ link.title }}
              </v-btn>
              <br :key="'br' + j" />
            </template>
          </v-col>
          <v-spacer></v-spacer>
          <v-col cols="12" md="4" class="text-center text-md-right">
            <span class="body-2 d-block">
              立即下載我們的App，搵盤更自由！
            </span>
            <v-row justify="center" justify-md="end" class="ma-2">
              <v-sheet rounded class="white" height="70" width="70">
                QR Code
              </v-sheet>

              <div>
                <v-sheet
                  outlined
                  rounded
                  class="pa-1 mx-2 d-block"
                  height="30"
                  width="100"
                >
                  Google play
                </v-sheet>
                <v-sheet
                  outlined
                  rounded
                  class="pa-1 mx-2 mt-1 d-block"
                  height="30"
                  width="100"
                >
                  App Store
                </v-sheet>
              </div>
            </v-row>
          </v-col>
        </v-row>
        <v-divider></v-divider>
        <v-row align="center" class="my-4 mx-sm-2">
          <span class="caption grey--text text--lighten-1"
            >&copy; Copyright {{ new Date().getFullYear() }} gagaking.com —
            版權所有</span
          >
          <br v-if="xs" />
          <span class="caption ml-1 ml-sm-4"><a href="">免責聲明</a></span>
          <span class="caption ml-1 ml-sm-4"><a href="">私隱政策</a></span>
          <v-spacer></v-spacer>
          <div>
            <v-btn v-for="(link, i) in socialLinks" :key="i" icon :to="link.to">
              <v-icon>{{ link.icon }}</v-icon>
            </v-btn>
          </div>
        </v-row>
      </v-container>
    </v-footer>
  </v-app>
</template>

<script>
import SearchBar from "~/components/SearchBar.vue";
export default {
  components: { SearchBar },
  data() {
    return {
      notifications: 2,
      links: [
        {
          title: "買樓",
          to: "/buy"
        },
        {
          title: "租樓",
          to: "/rent"
        },
        {
          title: "放盤",
          to: "/sell"
        },
        {
          title: "佢幫到你",
          to: "/assist"
        }
      ],
      footerLinks: [
        [
          {
            title: "買樓",
            to: "/buy"
          },
          {
            title: "租樓",
            to: "/rent"
          },
          {
            title: "放盤",
            to: "/sell"
          }
        ],
        [
          {
            title: "新聞動態",
            to: ""
          },
          {
            title: "公司簡介",
            to: ""
          },
          {
            title: "客戶服務",
            to: ""
          }
        ],
        [
          {
            title: "攻略blog",
            to: ""
          }
        ]
      ],
      socialLinks: [
        { icon: "mdi-facebook", to: "" },
        { icon: "mdi-instagram", to: "" },
        { icon: "mdi-linkedin", to: "" },
        { icon: "mdi-twitter", to: "" }
      ],
      right: true,
      rightDrawer: false,
      title: "GagaKing"
    };
  },
  computed: {
    xs() {
      return this.$vuetify.breakpoint.xsOnly;
    },
    toolbarLinks() {
      return this.$vuetify.breakpoint.mdAndUp ? this.$data.links : [];
    },
    navLinks() {
      return this.$data.links;
    }
  }
};
</script>
<style scoped>
.search-container {
  position: relative;
  top: 100%;
  height: 300%;
}
.footer-link {
  flex: 1 0 calc(100% / 3);
}
</style>
