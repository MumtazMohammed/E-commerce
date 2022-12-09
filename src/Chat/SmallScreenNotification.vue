<template>
  <div class="Notification">
    <!-- <v-app-bar class="" app>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="20">mdi-bell-outline</v-icon>
        الأشعارات
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar> -->
    <v-card flat tile>
      <v-toolbar color="#fc624d" dark extended flat>
        <v-toolbar-title style="flex-basis: 80%" class="toolbar-title">
          الأشعارات
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn to="/TheUserPageView" icon>
          <v-icon size="30">mdi-arrow-left-thin</v-icon>
        </v-btn>
      </v-toolbar>
      <v-card
        class="mx-auto"
        outlined
        max-width="97%"
        style="margin-top: -60px"
      >
        <v-toolbar flat>
          <v-toolbar-title style="flex-basis: 80%" class="grey--text">
            <v-text-field
              placeholder="بحث"
              dense
              solo
              flat
              hide-details
            ></v-text-field>
          </v-toolbar-title>
          <v-spacer></v-spacer>
          <v-btn icon>
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </v-toolbar>
        <v-divider></v-divider>
        <v-card
          class="pa-2 overflow-y-auto tile overflow-x-hidden"
          style="height: calc(100vh - 105px)"
          v-scroll.self="onScroll"
        >
          <v-dialog v-model="dialog" persistent fullscreen>
            <template v-slot:activator="{ on, attrs }">
              <v-card
                v-bind="attrs"
                v-on="on"
                flat
                class="users-card ma-1"
                v-for="n in 20"
                :key="n"
              >
                <v-card-actions class="pa-0 px-1">
                  <v-avatar rounded="" size="30" color="red"> </v-avatar>
                  <div>
                    <v-card-title class="pa-0 pr-2 d users-Name text-truncate">
                      محمد أمين شمسان
                    </v-card-title>
                    <v-card-text
                      class="pa-0 pr-2 users-Message text--disabled text-truncate"
                    >
                      محمد أمين شمسان
                    </v-card-text>
                  </div>
                  <v-spacer></v-spacer>
                  <span class="unred-message">5</span>
                </v-card-actions>
                <v-divider inset></v-divider>
              </v-card>
            </template>
            <v-app-bar class="" app>
              <v-toolbar-title class="user-title"> أسم المتجر </v-toolbar-title>
              <v-spacer></v-spacer>
              <v-btn @click="dialog = false" icon>
                <v-icon size="30">mdi-arrow-left-thin</v-icon>
              </v-btn>
            </v-app-bar>
            <v-sheet
              v-scroll.self="onScroll"
              class="overflow-y-auto my-12 overflow-x-hidden pa-1"
              style="height: calc(100vh - 57)"
              color="grey lighten-3"
            >
              <v-col class="text-center" cols="12">
                <span class="grey--text">14/3</span>
              </v-col>
              <v-col class="pa-1 text-right" cols="12" v-for="n in 15" :key="n">
                <v-card
                  flat
                  dark
                  color="teal darken-1"
                  style="width: fit-content; max-width: 250px"
                  class="pa-2 rounded-lg rounded-br-0 message"
                >
                  رسالتيرسالتيرسالتيرسالتيرسالتي رسالتيرسالتيرسالتيرسالتيرسالتي
                </v-card>
                <span class="message-time">05:20</span>
              </v-col>
              <v-col class="pa-1 text-left" cols="12" v-for="n in 20" :key="n">
                <v-card
                  flat
                  color=""
                  style="
                    width: fit-content;
                    margin-right: auto;
                    max-width: 250px;
                  "
                  class="pa-2 rounded-lg rounded-bl-0 message"
                >
                  رسالة الآخر رسالة الآخر رسالة الآخر رسالة الآخر رسالة الآخر
                  رسالة الآخر
                </v-card>
                <span class="message-time">05:20</span>
              </v-col>
            </v-sheet>
            <v-bottom-navigation class="align-center" app horizontal>
              <v-btn color="transparent" class="elevation-0">
                <v-icon class="grey--text ma-0">mdi-emoticon-outline</v-icon>
              </v-btn>
              <v-btn
                :class="message.length >= 1 ? 'send-message' : 'write-message'"
                color=""
              >
                <v-icon color="#fc624d" class="ma-0"> mdi-send </v-icon>
              </v-btn>
              <v-text-field
                flat
                v-model="message"
                placeholder="رسالة"
                dense
                hide-details
                solo
                max-width="80%"
              ></v-text-field>

              <v-btn color="transparent" class="elevation-0">
                <v-icon class="grey--text ma-0">mdi-paperclip</v-icon>
              </v-btn>
            </v-bottom-navigation>
          </v-dialog>
        </v-card>
      </v-card>
    </v-card>
  </div>
</template>
<script>
export default {
  components: {},
  name: "Notification",
  data() {
    return {
      scrollInvoked: 0,
      dialog: false,
      message: "",
    };
  },
  methods: {
    onScroll() {
      this.scrollInvoked++;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Notification {
  width: 100%;
  height: 100vh;
  .users-card:hover {
    background-color: #eee;
  }
  .users-Name {
    font-size: 13px !important;
    font-family: $fontfamliy3;
    // width: 100px;
  }

  .users-Message {
    font-size: 12px !important;
    font-family: $fontfamliy3;
    display: block !important;
  }
  .unred-message {
    min-width: 35px;
    height: 18px;
    background-color: $color-2;
    color: #fff;
    border-radius: 5px;
    font-size: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
.message {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 13px;
  text-align: justify;
  line-height: 1.5;
}
.message-time {
  font-size: 10px;
  // margin-top: 5px;
}
::v-deep input#input-11::placeholder {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
}
::v-deep .v-dialog__content.v-dialog__content--active {
  z-index: 1000;
}
::v-deep .v-input__slot {
  background-color: #eee !important;
}
::v-deep header.v-sheet.theme--light.rounded-0.v-toolbar.grey.lighten-3 {
  z-index: 1;
}
::v-deep .v-item-group.v-bottom-navigation .v-btn {
  background-color: transparent;
  border-radius: 0;
  box-shadow: none;
  flex: 0 1 auto;
  font-size: 0.75rem;
  height: inherit;
  max-width: 40px;
  min-width: 33px;
  position: relative;
  text-transform: none;
}
::v-deep .v-toolbar__content .toolbar-title {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: #fff !important;
  font-size: 17px !important;
  font-weight: 600;
}
::v-deep .v-toolbar__content .user-title {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
  font-size: 17px !important;
  font-weight: 600;
}
.send-message {
  max-width: 40px !important;
  min-width: 33px !important;
  transition: all 0.1s 0s ease-out;
}
.write-message {
  max-width: 0 !important;
  min-width: 0px !important;
  padding: 0 !important;
  overflow: hidden;
  transition: all 0.1s 0s ease-in;
}
</style>
