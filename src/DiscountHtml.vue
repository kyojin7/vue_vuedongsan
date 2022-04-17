<template>
    <div class="discount">
        <h4>지금 결제하면 {{ counting }}% 할인</h4>
    </div>
</template>

<script>
export default {
    name:'DiscountHtml',
    data(){
        return{
            counting: 30
        }
    },
    mounted(){
        setInterval(() => {
            this.counting -= 1
        }, 1000)
    },
}
</script>

<style>
.discount{
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
</style>