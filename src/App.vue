<template>

<!-- modal 만들기 -->
<!-- <div @mousedown="modal.isOpen=false" class="black-bg" v-if="modal.isOpen">
  <div class="white-bg">
    <img :src="modal.contents.image" class="modal-image">
    <h4>{{modal.contents.title}}</h4>
    <p>{{modal.contents.content}}</p>
    <p>가격 : {{modal.contents.price}}원</p>
    <discount-banner/>
  </div>
</div> -->

<Modal 
  :isOpen="modal.isOpen" 
  :contents="modal.contents" 
  @modalClose="modal.isOpen=false"></Modal>

<!-- 메뉴 만들기 -->
  <div class="menu">
    <a v-for="(link,i) in menu.link" :key="'menu-'+i" :href="menu.link[i]">{{menu.name[i]}}</a>
  </div>

  <discount-banner/>
  <Card v-for="(oneroom, i) in onerooms" 
    :key="'oneroom-'+i"
    :product="oneroom"
    @modalOpen="modal.isOpen=true;modal.contents=oneroom"></Card>

  <!-- <div v-for="(oneroom, i) in onerooms" :key="'oneroom-'+i">
    <img :src="oneroom.image" class="room-img">
    <h4 @click="modal.isOpen=true;
                modal.contents=oneroom">{{oneroom.title}}</h4>
    <p>{{oneroom.price}} 원</p>
  </div> -->

  <!-- <div v-for="(a, i) in products.product" :key="'product-'+i">
    <img :src="require('./assets/room'+i+'.jpg')" class="room-img">
    <h4 @click="modal.isOpen=true">{{products.product[i]}}</h4>
    <p>{{products.price[i]}} 만원</p>
    <button @click="reportFakeProduct(i)">허위매물신고</button> <span>신고수 : {{ products.fakeReport[i] }}</span>
  </div> -->


</template>

<script>
import OneRooms from './assets/oneroom.js'
import DiscountBanner from './components/DiscountBanner.vue'
import ModalComponent from './components/Modal.vue'
import CardComponent from './components/CardComponent.vue'
export default {
  name: 'App',
  data(){
    return {
      onerooms : OneRooms,
      modal : {
        clicked : 0,
        isOpen : false,
        title : '',
        contents : {},
      },
      menu : {
        name : ['HOME', 'PRODUCTS', 'ABOUT'],
        link : ['#', '#', '#']
      },
      products : {
        product : ['역삼동원룸', '천호동원룸', '마포구원롬'],
        price : [60, 30, 70],
        fakeReport : [0,0,0]
      },

    }
  },
  methods : {
    reportFakeProduct(i){
      this.products.fakeReport[i] += 1;
    },
    discountPrice(){
      this.price1 = this.price1/2;
      this.price2 = this.price2/2;
    }
  },
  components: {
    DiscountBanner : DiscountBanner,
    Modal: ModalComponent,
    Card :CardComponent,
  }
}
</script>

<style>
body{
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rbga(0,0,0,0.5);
  position: fixed;
  margin-top: 100px;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: rgb(255, 255, 255);
  border-radius: 8px;
  padding: 20px;
}
.modal-image{
  width: 100%;
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
  text-align: left;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
