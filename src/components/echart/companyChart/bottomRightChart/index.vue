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
                // electric: [120, 132, 101, 134, 90, 230, 210, 154, 267, 310, 245, 130],
                // energy: [220, 182, 191, 234, 290, 330, 310, 245, 130, 236, 150, 126],
                env: [15, 23, 20, 15, 19, 33, 41, 24, 18, 30, 23, 29, 33],
                safe: [32, 33, 30, 33, 39, 33, 32, 23, 20, 30, 31, 23],
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