<template>
    <div>
             <!-- Header Section Begin -->
    <header class="header-section">
        <div class="header-top">
            <div class="container">
                <div class="ht-left">
                    <div class="mail-service">
                        <i class=" fa fa-envelope"></i> hello.shayna@gmail.com
                    </div>
                    <div class="phone-service">
                        <i class=" fa fa-phone"></i> +628 22081996
                    </div>
                </div>
            </div>
        </div>
        <div class="container">
            <div class="inner-header">
                <div class="row">
                    <div class="col-lg-2 col-md-2">
                        <div class="logo">
                            <a href="./index.html">
                                <img src="img/logo_website_shayna.png" alt="" />
                            </a>
                        </div>
                    </div>
                    <div class="col-lg-7 col-md-7"></div>
                    <div class="col-lg-3 text-right col-md-3">
                        <ul class="nav-right">
                            <li class="cart-icon">
                                Keranjang Belanja &nbsp;
                                <a href="#">
                                    <i class="icon_bag_alt"></i>
                                    <span>{{keranjangUser.length}}</span>
                                </a>
                                <div class="cart-hover">
                                    <div class="select-items">
                                        <table>
                                            <tbody v-if="keranjangUser.length > 0">

                                                <tr v-for="keranjang in keranjangUser" :key="keranjang.id">
                                                    <td class="si-pic">
                                                        <img class="photo-item" :src="keranjang.photo" alt="" />
                                                    </td>
                                                    <td class="si-text">
                                                        <div class="product-selected">
                                                            <p>${{keranjang.price}} x 1</p>
                                                            <h6>{{keranjang.name}}</h6>
                                                        </div>
                                                    </td>
                                                    <td @click="removeItem(keranjang.id)" class="si-close">
                                                        <i class="ti-close"></i>
                                                    </td>
                                                </tr>
                                                
                                            </tbody>
                                            <tbody v-else>
                                                <tr>
                                                    <td>Keranjang Kosong</td>
                                                </tr>
                                            </tbody>
                                        </table>
                                    </div>
                                    <div class="select-total">
                                        <span>total:</span>
                                        <h5>${{ totalHarga}}.00</h5>
                                    </div>
                                    <div class="select-button">
                                        <a href="#" class="primary-btn view-card" ><router-link to="/shoppingcart" style="color: #FFF;">
                                        VIEW CARD
                                        </router-link></a>
                                        <a href="#" class="primary-btn checkout-btn">CHECK OUT</a>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </header>
    <!-- Header End -->
    </div>
</template>

<script>
export default {
  name: 'HeaderShayna',
    data(){
      return{
         
          keranjangUser:[]
      }
  },

  methods : {
      removeItem(idx){
          //cari tahu dari si item yang akan dihapus
           let keranjangUserStorge = JSON.parse(localStorage.getItem('keranjangUser'));
           let ItemKeranjangUserStorage = keranjangUserStorge.map(ItemKeranjangUserStorage => ItemKeranjangUserStorage.id);
           //cocokkan id item dengan id yang ada di storage
           let index = ItemKeranjangUserStorage.findIndex(id => id == idx);
           this.keranjangUser.splice(index, 1);
            //jika sudah dihapus, update ke local storage
            const parsed = JSON.stringify(this.keranjangUser);
            localStorage.setItem('keranjangUser', parsed);

            //kodingan di bawah ini untuk mereload kembali/ refresh kembali halaman
            window.location.reload();
      }
  },
  mounted(){
           if (localStorage.getItem('keranjangUser')) {
      try {
        this.keranjangUser = JSON.parse(localStorage.getItem('keranjangUser'));
      } catch(e) {
        localStorage.removeItem('keranjangUser');
      }
    }
  },

  computed : {
      totalHarga(){
          return this.keranjangUser.reduce(function(items, data){
              return items + data.price;
          },0);
      }
  }
 
}
</script>
<style scoped>
    .photo-item 
    {
        width: 80px;
        height: 80px;
    }  
</style>