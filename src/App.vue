<template>

  <!-- 모달창 -->
  <!-- modalYn이 true일때만 end class가 적용됨 -->
  <!-- <div class="start" :class="{ end:modalYn }">  -->
  <transition name="fade">
    <ModalHtml @closeModal="modalYn=false" :detailData = 'detailData' :modalYn = 'modalYn' />
  </transition>
  <!-- </div> -->

  <!-- 메뉴 -->
  <div class="menu">
    <a v-for="(a, i) in menuList" :key="i">{{a}}</a>
  </div>

  <!-- 배너 -->
  <DiscountHtml v-if="showDiscount == true"/>

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">초기화</button>

  <!-- 본문 -->
  <CardHtml @doModal="modalYn=true; setDetail($event)" :oneroomData = 'oneroomData' />

</template>

<script>
import jsData from './assets/oneroom.js'
import DiscountHtml from './DiscountHtml.vue'
import ModalHtml from './ModalHtml.vue'
import CardHtml from './CardHtml.vue'

export default {
  name: 'App',
  data(){
    return {
      showDiscount: true,
      detailData: [],
      oneroomData: jsData,
      oneroomDataOri: [...jsData],
      modalYn: false,
      menuList : ['Home', 'Shop', 'About'],
    }
  },
  methods:{
    priceSort(){
      this.oneroomData.sort(function(a,b){
        return a.price - b.price
      })
    },
    sortBack(){
      this.oneroomData = [...this.oneroomDataOri]
    },
    setDetail(i){
      console.log('++')
      this.detailData = []
      this.detailData.push({
        detailTitle: this.oneroomData[i].title,
        detailContent: this.oneroomData[i].content,
        detailImg: this.oneroomData[i].image,
        detailPrice: this.oneroomData[i].price
      })
    },
    reportIncrease(){
      this.reportCount++
    }
  },

  components: {
    DiscountHtml : DiscountHtml,
    ModalHtml : ModalHtml,
    CardHtml : CardHtml,
  }
}
</script>


<style>
.fade-leave-from{
  opacity: 0;
}
.fade-leave-active{
  transition: all 1s;
}
.fade-leave-to{
  opacity: 1;
}
.fade-enter-from{
  opacity: 0;
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  opacity: 1;
}

.start{
  opacity: 0;
  transition: all 1s;
}
.end{
  opacity: 1;
}

.detail-img{
  width: 40%;
}
.body{
  margin: 0;
}
.div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
.room-img{
  width: 40%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
</style>
