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
                total: [120, 132, 101, 134, 90, 230, 210, 154, 267, 310, 245, 130],
                // consume: [220, 182, 191, 234, 290, 330, 310, 245, 130, 236, 150, 126],
                // added: [150, 232, 201, 154, 190, 330, 410, 245, 182, 301, 234, 290, 330],
                // business: [320, 332, 301, 334, 390, 330, 320, 332, 301, 304, 310, 230],
                // personal: [820, 932, 901, 934, 1290, 1330, 1320, 2000 ,2300, 2450, 3000, 2600]
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