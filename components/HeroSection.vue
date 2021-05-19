<template>
  <v-col
    :class="{ 'wide-layout': wideLayout, reverse: reverse }"
    md="10"
    offset-md="1"
    xs="12"
  >
    <v-col class="heading" align-self="end">
      <slot name="heading"></slot>
    </v-col>

    <v-container class="img" v-if="hasImg">
      <slot name="img"></slot>
    </v-container>

    <v-container class="body">
      <slot name="body"></slot>
    </v-container>
  </v-col>
</template>

<script>
export default {
  props: {
    wide: {
      type: Boolean,
      default: true
    },
    reverse: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    wideLayout() {
      return this.$props.wide && !this.$vuetify.breakpoint.xsOnly;
    },
    hasImg() {
      return !!this.$slots["img"];
    }
  }
};
</script>

<style lang="scss" scoped>
.wide-layout {
  display: grid;
  column-gap: 12%;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto auto;
  grid-template-areas:
    "heading img"
    "body img";
  &.reverse {
    grid-template-areas:
      "img heading"
      "img body";
  }
  .heading {
    grid-area: heading;
  }
  .body {
    grid-area: body;
  }
  .img {
    grid-area: img;
  }
}
</style>
