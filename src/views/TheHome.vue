<template>
  <v-main class="main">
    <NavBar />
    <OutAdvertisement />
    <Services />
    <TheCategorieSmallScreen />
    <BestOffer />
    <DailyOffer />
    <TopSale />
    <CompaniesCardAdv />
    <YouMightLikeIt />
    <!-- <CarBrands :AllDateCar="AllDateCar" />
    <CarShape :AllDateCar="AllDateCar" /> -->
    <!-- <CarPartsCategories /> -->
    <!-- <HowToBuy /> -->
    <!-- <ContactUs /> -->
    <FixedBottomNav class="hidden-sm-and-up" />
  </v-main>
</template>

<script>
import FixedBottomNav from "../NavBar/FixedBottomNav.vue";
import NavBar from "@/NavBar/TheNavBar.vue";
import TheCategorieSmallScreen from "../A-Home/TheCategorieSmallScreen.vue";
import OutAdvertisement from "@/Advertisement/OutAdvertisement.vue";
import BestOffer from "../A-Home/BestOffer.vue";
import DailyOffer from "../A-Home/DailyOffer.vue";
import TopSale from "../A-Home/TopSale.vue";
import Services from "../A-Home/Services.vue";
import CompaniesCardAdv from "../A-Home/CompaniesCardAdv.vue";
import YouMightLikeIt from "../A-Home/YouMightLikeIt.vue";
// import CarPartsCategories from "../A-Home/CarPartsCategories.vue";
import DateCar from "../data-json/car-data.json";
import AllDateCar from "../data-json/All-Car.json";
import CarType from "../data-json/CarType.json";

const components = {
  OutAdvertisement,
  Services,
  CompaniesCardAdv,
  TheCategorieSmallScreen,
  BestOffer,
  DailyOffer,
  TopSale,
  YouMightLikeIt,
  NavBar,
  FixedBottomNav,
};
export default {
  name: "Home",
  components,
  data() {
    return {
      caritems: DateCar,
      AllDateCar,
      CarType: CarType,
    };
  },
};
</script>
<style lang="scss" scoped>
.main {
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
}
</style>
