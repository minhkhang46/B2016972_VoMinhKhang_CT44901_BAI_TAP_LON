<template>
   <div class="wrapper">
      <div class="header">
         <div class="nav-menu">
            <NavMenu />
         </div>
      </div>
      <div class="container">
         <div class="slider">
            <BaseSlider />
         </div>
         <div class="listcategory">
            <ProductScreen />
         </div>
      </div>
      <!-- <div class="container">
         <div class="Menu">
            <SideBrand />
         </div>
      </div> -->
      <BaseFooter />
   </div>
</template>

<script>
import NavMenu from "../components/NavMenu.vue";
import BaseSlider from "../components/BaseSlider.vue";
import ProductScreen from "../components/ProductScreen.vue";
import SideBrand from "../components/SideBrand.vue";
import BaseFooter from "../components/BaseFooter.vue";

export default {
   name: "Home",
   components: {
      NavMenu,
      BaseSlider,
      ProductScreen,
      SideBrand,

      BaseFooter
   },
};
</script>

<style scoped>
.wrapper {
   max-width: 100%;
   background: #fff;
   font-family: "Open Sans", sans-serif;
   padding-top: 5px;
   box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
.header {
   width: 100%;
   height: auto;
}
.container {
   width: 100%;
   height: auto;
   margin-top: 5px;
   margin-bottom: 20px;
}
.slider {
   width: 100%;
   height: auto;
}
.listcategory {
   width: 100%;
   height: auto;
}
.slider-brand {
   width: 100%;
   height: 150px;
}
</style>
