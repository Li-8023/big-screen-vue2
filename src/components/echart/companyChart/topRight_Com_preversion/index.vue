<template>
    <div>
        <Chart :cdata="cdata"/>
    </div>
</template>

<script>
import Chart from './chart.vue'
export default {
    data(){
        return {
            cdata: {
                category:["一月", "二月", "三月", "四月", "五月", "六月", "七月", "八月", "九月", "十月", "十一月", "十二月"],
                electric: [120, 132, 101, 134, 90, 230, 210, 154, 267, 310, 245, 130],
                energy: [220, 182, 191, 234, 290, 330, 310, 245, 130, 236, 150, 126],
                env: [150, 232, 201, 154, 190, 330, 410, 245, 182, 301, 234, 290, 330],
                safe: [320, 332, 301, 334, 390, 330, 320, 332, 301, 304, 310, 230],
              
            }
        };
    },
    components: {
        Chart,
    },
    mounted() {
        this.setData();
    }

}

</script>

<style lang="scss" scoped>
</style>