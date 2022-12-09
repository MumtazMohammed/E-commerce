<template>
  <div class="UserAdd">
    <v-app-bar class="mb-5" app>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="20">mdi-plus-circle-outline </v-icon>
        نقاطي
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <div class="mt-15">
      <v-card-text class="points-text-total">
        لديك <span>500</span> نقطة
      </v-card-text>

      <v-sheet v-for="item in 15" :key="item" outlined class="pa-1 mb-2 mx-3">
        <v-card-actions class="justify-start align-start pa-0">
          <v-avatar
            class="avatar my-auto"
            size="50"
            tile
            color="yellow darken-2"
          >
            <v-img
              contain
              src="@/assets/Mazda/mazda1.jpg"
              alt="@/assets/Hyundai/image2.jpg"
            ></v-img>
          </v-avatar>
          <v-card-actions class="flex-column align-start pa-0">
            <span class="title mr-2 grey--text text--darken-2">
              مـازدا مازدا3
            </span>
            <v-card-text
              class="recount pa-0 text-truncate pr-2 grey--text text--darken-1"
            >
              <span class="mx-1"> 2 </span>
              ,
              <span class="mx-1"> احمر</span>
              ,
              <span class="mx-1"> ee02121</span>
              ,
              <span class="mx-1"> (15 - 18) </span>
            </v-card-text>
          </v-card-actions>
          <v-spacer></v-spacer>
          <v-card-title
            style="pointer-events: none; font-size: 15px"
            class="pa-0 my-auto yellow--text text--darken-2"
          >
            10+
          </v-card-title>
        </v-card-actions>
      </v-sheet>
    </div>
  </div>
</template>
<script>
export default {
  name: "UserAdd",
  components: {},
  data() {
    return {
      text: "هل أنت متأكد من حذف الأعلان.",
      tab: null,
    };
  },
  methods: {
    customFilter(item, queryText) {
      const textOne = item.name.toLowerCase();
      const textTwo = item.abbr.toLowerCase();
      const searchText = queryText.toLowerCase();

      return (
        textOne.indexOf(searchText) > -1 || textTwo.indexOf(searchText) > -1
      );
    },
    save() {
      this.hasSaved = true;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.UserAdd {
  width: 100%;
  // padding: $padding;
  min-height: 75vh;
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 16px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: $color-2 !important;
      margin-left: 5px;
    }
  }
  .title {
    font-family: $fontfamliy !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 16px !important;
  }
  .recount {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 13px !important;
    font-weight: 600;
  }
  .links {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600;
    font-size: 15px !important;
  }
  .links:hover {
    color: $color-2 !important;
  }
  .links-active {
    color: $color-2 !important;
  }

  .points-text-total {
    font-family: $fontfamliy !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 16px !important;
    color: #43a047;
  }
}
</style>
