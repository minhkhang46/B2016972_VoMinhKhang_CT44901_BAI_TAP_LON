<template>
   <div class="row">
   
   </div>
   <div class="slider-box">
      <div class="slider-content">
         <Splide :options="options" aria-label="My Favorite Images">
            <SplideSlide>
               <img src="../images/slider/dong-ho-nam-ban-chay.jpg" alt="Sample 2" />
            </SplideSlide>
            <SplideSlide>
               <img src="../images/slider/dong-ho-nu-ban-chay.jpg" alt="Sample 1" />
            </SplideSlide>
            <SplideSlide>
               <img src="../images/slider/bst-fossil-jacqueline-three-hand.jpg" alt="Sample 3" />
            </SplideSlide>
            <SplideSlide>
               <img src="../images/slider/bst-tissot-prx.jpg" alt="Sample 4" />
            </SplideSlide>
            <SplideSlide>
               <img src="../images/slider/banner-danh-muc_SEIKO-SINCE-1881.jpg" alt="Sample 4" />
            </SplideSlide>

         </Splide>
      </div>
   </div>
</template>

<script>
import { Splide, SplideSlide } from "@splidejs/vue-splide";
import { defineComponent } from "vue";

export default defineComponent({
   components: {
      Splide,
      SplideSlide,
   },

   setup() {
      const options = {
         rewind: true,
         gap: "1rem",
         autoplay: true,
      };

      return { options };
   },
});
</script>

<style scoped>

.row {
   padding-top: 0px;
   /* padding: 0px; */
}

.page{
   padding: 0px;
}

.splide__slide img {
   width: 100%;
   height: 500px;
   object-fit: cover; /* Bao phủ toàn bộ khung hình */
   display: block;
}
.content {
   margin-top: 5px;
   position: absolute; /* Để đưa nội dung vào trong khung ảnh */
   right: 10px;
   bottom: 20px;
   width: 400px;
   text-align: justify;
   background-color: #333;
   padding: 7px 7px 12px;
   border-radius: 3px;
   opacity: 0.85;
}
.content a {
   text-decoration: none;
   color: white;
   display: inline-block;
   line-height: 24px;
   text-transform: uppercase;
}
</style>
