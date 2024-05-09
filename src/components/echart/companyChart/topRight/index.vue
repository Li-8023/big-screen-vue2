<template>
    <div>
        <Chart :cdata="cdata" />
    </div>
</template>

<script>
import Chart from './chart.vue'
export default {
    data(){
        return{
            cdata: {
                category: ["一月", "二月", "三月", "四月", "五月", "六月", "七月", "八月", "九月", "十月", "十一月", "十二月"],
                num:[320, 332, 301, 334, 390, 330, 320, 332, 301, 304, 310, 230],
            }
        };
    },
    components:{
        Chart,
    },
    mounted(){
        this.setData();
    }
}
</script>
<style lang="scss" scoped>
</style>