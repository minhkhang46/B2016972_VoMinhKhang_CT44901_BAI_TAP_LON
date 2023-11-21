<template>
   <div class="wrapper">
      <div class="header">
         <div class="nav-menu">
            <NavMenu />
         </div>
      </div>
      <div class="container">
         <div class="row contact">
            <div class="col-sm-6">
               <p>
                  <i class="fa-solid fa-location-dot"></i>
                  <a href="https://ctu.edu.vn">
                     Trường Đại Học Cần Thơ Khu II, Đ. 3/2, Xuân Khánh, Ninh Kiều, Cần
                     Thơ
                  </a>
               </p>
               <p>
                  <i class="fa-solid fa-school"></i>
                  Trường công nghệ thông tin và truyền thông
               </p>
               <p>
                  <i class="fa-solid fa-envelope icon-email"></i>
                  <a style="color: #000;text-decoration: none;" href="mailto:minhkhang@gmail.com">  minhkhang@gmail.com</a>

               </p>
               <p>
                  <i class="fa-solid fa-phone icon-phone"></i>
                  <a style="color: #000;text-decoration: none;" href="tel:+84 56668888">  +84 56668888</a>
               </p>
            </div>
            <div class="col-sm-6">
               <iframe class="map"
                  src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d15715.309578979477!2d105.76044688128938!3d10.031098185838209!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31a0883d2192b0f1%3A0x4c90a391d232ccce!2zVHLGsOG7nW5nIEPDtG5nIE5naOG7hyBUaMO0bmcgVGluIHbDoCBUcnV54buBbiBUaMO0bmcgKENUVSk!5e0!3m2!1svi!2s!4v1680923439730!5m2!1svi!2s"
                  width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy"
                  referrerpolicy="no-referrer-when-downgrade"></iframe>
            </div>
         </div>
         <!-- gui yeu cau -->
      </div>
   </div>
</template>

<script>
import NavMenu from "../components/NavMenu.vue";

export default {
   components: {
      NavMenu,
   },
   methods: {
      feedback() {
         alert("Cảm ơn bạn đã đóng góp ý kiến!!");
      },
   },
};
</script>

<style scoped>
/* .wrapper {
   max-width: 100%;
   background-color: #fff;
   font-family: "Open Sans", sans-serif;
   padding-bottom: 50px;
   padding-top: 5px;
   box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
} */

.footer {
   margin-top: 100px;
}

.header {
   width: 100%;
   height: auto;
}

.container {
   text-align: left;
   margin-top: 5px;
   color: #333;

}

.form-group {
   padding-left: 15px;
}

.map {
   padding: 0 15px;
   width: 100%;
}

.contact {
   margin-top: 10px;
   padding-left: 15px;
}

</style>