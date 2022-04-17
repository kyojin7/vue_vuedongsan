<template>
    <div class="black-bg" v-if="modalYn == true">
        <div class="white-bg">
            <h4>{{detailData[0].detailTitle}}</h4>
            <img :src="detailData[0].detailImg" class="detail-img">
            <p>{{detailData[0].detailContent}}</p>
            <input v-model.number="month">
            <p>{{month}}개월 선택함 : {{detailData[0].detailPrice * month}} 원</p>
            <button @click="this.$emit('closeModal')">X Close</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ModalHtml',
    data(){
      return{
          month: 1,
          checkYN: false,
      }  
    },
    beforeUpdate(){
        if(this.month == 2){
            alert('2개월은 안됩니다')
            this.month = 3
        }
    },
    watch:{
        month(a){
            if(a > 12){
                alert('13이상 입력하지마세요')
            }
        },

    },
    props : {
        detailData : Array,
        modalYn: Boolean
    }
}
</script>

<style>

</style>