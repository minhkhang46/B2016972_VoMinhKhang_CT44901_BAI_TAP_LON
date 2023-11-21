<template>
   <div class="wrapper">
      <div class="header">
         <div class="nav-menu">
            <NavMenu />
         </div>
      </div>
      <div class="container">
         <div class="customer-info">
            <h2>Thông tin khách hàng</h2>
            <form @submit.prevent="placeOrder">
               <div class="form-group">
                  <label for="name">Họ và Tên:</label>
                  <input type="text" id="name" class="form-control" v-model="customer.name" required>
               </div>
               <div class="form-group">
                  <label for="txtTelephone">Số Điện Thoại:</label>
                  <input type="tel" id="txtTelephone" class="form-control" v-model="customer.txtTelephone" required>
               </div>
               <div class="form-group">
                  <label for="address">Địa chỉ giao hàng:</label>
                  <input id="address" class="form-control" v-model="customer.address" required>
               </div>
            </form>
         </div>
         <div class="px-3 py-3 pr-3 mx-auto float-left">
            <span class="btn btn-success">
               Số sản phẩm: {{ products.length }}
            </span>
         </div>
         <table class="table table-bordered table-striped table-sm">
            <thead>
               <tr class="table-active text-center">
                  <th scope="col">STT</th>
                  <th scope="col">Hình ảnh</th>
                  <th scope="col" class="space-name">Tên sản phẩm</th>
                  <th scope="col" class="space-price">Giá</th>
                  <th scope="col" class="space-amount">Số lượng</th>
                  <th scope="col" class="space-total">Thành tiền</th>
                  <th scope="col" class="space-handle">Xử lý</th>
               </tr>
            </thead>
            <tbody>
               <tr :key="index" v-for="(product, index) in products">
                  <td class="items-center text-center">{{ index + 1 }}</td>
                  <td>
                     <img class="product-img" :src="product.imgUrl" alt="" />
                  </td>
                  <td class="items-center">
                     {{ product.name }} {{ product.description }}
                  </td>
                  <td class="items-center text-center">
                     {{ product.price.replace(/\B(?=(\d{3})+(?!\d))/g, ".") }}
                     đồng
                  </td>
                  <td class="items-center text-center"><input class="amount" min="0" type="number" v-model="product.amount"/></td>
                  <td class="items-center text-center">
                     {{
                        `${product.price * product.amount}`.replace(
                           /\B(?=(\d{3})+(?!\d))/g,
                           "."
                        )
                     }}
                     đồng
                  </td>
                  <td class="items-center text-center">
                     <button
                        v-if="product.id"
                        type="button"
                        class="ml-2 btn btn-danger"
                        @click="deleteProductCart(index)"
                     >
                        Xóa
                     </button>
                  </td>
               </tr>
            </tbody>
         </table>
         <div class=" order">
            <div class=" px-2 py-3 pr-3 mx-auto float-right">
               <button class="btn btn-success">
                  Tổng Tiền:
                  {{
                     `${totalPrice().replace(/\B(?=(\d{3})+(?!\d))/g, ".")} đồng`
                  }}
               </button>
               <br>
               <button class="btn btn-success mt-2 mx-auto float-right" @click="placeOrder">Đặt hàng</button>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
import NavMenu from "../components/NavMenu.vue";

export default {
   components: {
      NavMenu,
   },
  data() {
    return {
      products: [],
      customer: {
        name: '',
        txtTelephone: '',
        address: ''
      }
    };
  },
  methods: {
    deleteProductCart(index) {
      // Xóa sản phẩm khỏi giỏ hàng
      this.products.splice(index, 1);
      this.saveProductCartToLocalStorage();
    },
    totalPrice() {
      let total = 0;
      for (let i = 0; i < this.products.length; i++) {
        total += this.products[i].price * this.products[i].amount;
      }
      return `${total}`;
    },
    placeOrder() {
      // Kiểm tra xem có sản phẩm trong giỏ hàng không
      if (this.products.length === 0) {
        alert('Giỏ hàng trống! Vui lòng thêm sản phẩm vào giỏ hàng.');
        return;
      }

      // Kiểm tra thông tin khách hàng
      if (!this.customer.name || !this.customer.txtTelephone || !this.customer.address) {
        alert('Vui lòng nhập đầy đủ thông tin khách hàng.');
        return;
      }

      // Xử lý đặt hàng ở đây
      // ...

      // Reset giỏ hàng và thông tin khách hàng
      this.products = [];
      this.customer = {
        name: '',
        email: '',
        address: ''
      };
      this.saveProductCartToLocalStorage();

      // Hiển thị thông báo hoặc chuyển hướng đến trang xác nhận đặt hàng thành công
      alert('Đặt hàng thành công!');

      // Hoặc chuyển hướng đến trang xác nhận đặt hàng thành công
      // window.location.href = '/xac-nhan-dat-hang';
    },
    saveProductCartToLocalStorage() {
      const localProductCart = JSON.stringify(this.products);
      localStorage.setItem("localProductCart", localProductCart);
    },
  },
  mounted() {
    const listLocalCart = JSON.parse(
      localStorage.getItem("localProductCart") ?? "[]"
    );
    this.products = listLocalCart;
  },
};
</script>
<style scoped>
.wrapper {

   background: #fff;
   font-family: "Open Sans", sans-serif;
   padding-bottom: 50px;
}
.header {
   width: 100%;
   /* height: 210px; */
   height: auto;
}
.container {
   background-color: #fff;
  
}
.amount{
   width: 50px;
}
.product-list {
   padding-bottom: 10px;
}
.product-img {
   width: 150px;
   height: auto;
}
a {
   text-decoration: none;
}
.button-add {
   color: #fff;
}
.space-price {
   width: 150px;
}
.space-amount {
   width: 100px;
}
.space-total {
   width: 150px;
}
.space-handle {
   width: 150px;
}
.items-center {
   padding-top: 45px;
}
.order{
   border-top: 2px solid #1190e4f5; 
}

.customer-info {
      max-width:100%;
      margin: 0 auto;
      padding: 20px;
      background-color: #f5f5f5;
      border: 1px solid #ddd;
      /* border-radius: 5px; */
   }

   .customer-info h2 {
      font-size: 24px;
      margin-bottom: 20px;
      text-align: center;
   }

   .customer-info .form-group {
      margin-bottom: 20px;
   }

   .customer-info label {
      display: block;
      font-weight: bold;
   }

   .customer-info input[type="text"],
   .customer-info input[type="tel"],
   .customer-info textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 4px;
   }

   .customer-info button[type="submit"] {
      background-color: #28a745;
      color: #fff;
      padding: 10px 20px;
      border: none;
      border-radius: 4px;
      font-size: 16px;
      cursor: pointer;
   }


</style>
