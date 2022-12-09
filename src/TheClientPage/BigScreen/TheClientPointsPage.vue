<template>
  <div class="UserAdd pb-4">
    <!-- car card  -->
    <v-container>
      <v-card-text class="points-text-total">
        لديك <span>500</span> نقطة
      </v-card-text>
      <!-- earned points  -->
      <v-row no-gutters>
        <v-col cols="4" md="3" sm="4" lg="3">
          <v-card flat class="ma-1 grey lighten-3">
            <v-img
              aspect-ratio="2.5"
              contain
              src="@/assets/Mazda/mazda1.jpg"
              alt="@/assets/Hyundai/image2.jpg"
              class="grey darken-3"
            ></v-img>
            <v-card-title
              class="title pa-0 text-truncate pr-3 grey--text text--darken-2"
            >
              مـازدا مازدا3
            </v-card-title>
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
            <v-spacer></v-spacer>
            <v-card-actions
              class="flex-column align-center justify-center my-auto pa-0"
            >
              <v-card-title
                style="pointer-events: none"
                class="pa-0 pr-2 yellow--text text--darken-2"
              >
                10+
              </v-card-title>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
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
  min-height: 100vh;

  .title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 16px !important;
    pointer-events: none;
    display: block;
  }
  .recount {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 13px !important;
    font-weight: 600;
    pointer-events: none;
    display: block;
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
    font-size: 17px !important;
    color: $color-2;
  }
}
</style>
