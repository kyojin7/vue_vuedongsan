<template>
    <div v-for="(room, i) in oneroomData" :key="i">
        <img :src="room.image" class="room-img">
        <!-- <h4 @click="openModal(); setDetail(i)">{{room.title}}</h4> -->
        <h4 @click="sendData(i)">{{room.title}}</h4>
        <p>{{room.price}} 만원</p>
    </div>
</template>

<script>
export default {
    name: 'CardHtml',
    props : {
        oneroomData : Array,
    },
    methods: {
        sendData(i){
            console.log('=====')
            this.$emit('doModal', i)
        },
    },
}
</script>

<style>

</style>