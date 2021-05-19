<template>
  <v-sheet
    :class="[{ 'rounded-pill': !embedded }, 'fill-height']"
    elevation="2"
  >
    <v-row align="center">
      <div class="ml-6">
        <chip-toggle
          :positiveText="'買'"
          :negativeText="'租'"
          v-model="searchChecked"
        ></chip-toggle>
      </div>
      <v-col class="py-sm-0" cols="6" sm="4">
        <v-text-field class="mb-n3"></v-text-field>
      </v-col>
      <v-spacer></v-spacer>
      <v-col
        class="py-sm-0"
        cols="1"
        md="auto"
        v-for="(menu, i) in menus"
        :key="i"
      >
        <v-menu
          open-on-hover
          offset-y
          min-width="200"
          content-class="menu-content"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              color="grey"
              class="menu-activator text-start py-0 pl-2 pr-10"
              text
              tile
              small
              v-bind="attrs"
              v-on="on"
            >
              <div class="menu-border"></div>
              {{ menu.name }}
            </v-btn>
          </template>

          <v-list dense>
            <template v-for="(section, j) in menu.sections">
              <v-subheader :key="'h' + j">{{ section.title }}</v-subheader>
              <v-list-item-group :key="'i' + j">
                <v-list-item
                  v-for="(item, index) in section.items"
                  :key="index"
                >
                  <v-list-item-icon class="mr-3">
                    <v-icon v-text="item.icon" color="primary"></v-icon>
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title v-text="item.text"></v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-group>
            </template>
          </v-list>
        </v-menu>
      </v-col>
      <v-spacer></v-spacer>
      <v-col class="mr-2 my-sm-2 py-sm-0 text-right">
        <v-btn color="primary" fab elevation="0" rounded small>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
      </v-col>
    </v-row>
  </v-sheet>
</template>

<script>
import ChipToggle from "./ChipToggle.vue";
export default {
  components: { ChipToggle },
  data() {
    return {
      searchChecked: false,
      menuData: [
        {
          name: "用途",
          sections: [
            {
              title: "街道",
              items: [
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖山莊"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxx"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxxx"
                }
              ]
            },
            {
              title: "街道",
              items: [
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖山莊"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxx"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxxx"
                }
              ]
            }
          ]
        },
        {
          name: "地區",
          sections: [
            {
              title: "街道",
              items: [
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖山莊"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxx"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxxx"
                }
              ]
            },
            {
              title: "街道",
              items: [
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖山莊"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxx"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxxx"
                }
              ]
            }
          ]
        },
        {
          name: "樓價",
          sections: [
            {
              title: "街道",
              items: [
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖山莊"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxx"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxxx"
                }
              ]
            },
            {
              title: "街道",
              items: [
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖山莊"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxx"
                },
                {
                  icon: "mdi-map-marker-outline",
                  text: "嘉湖xxxxx"
                }
              ]
            }
          ]
        }
      ]
    };
  },
  computed: {
    menus() {
      return this.$vuetify.breakpoint.smAndUp ? this.$data.menuData : [];
    }
  },
  props: ["embedded"]
};
</script>

<style>
.menu-activator {
  border-left: solid 2px lightgray;
}
.menu-content {
  border-bottom-left-radius: 24px;
  border-bottom-right-radius: 24px;
}
</style>
