<template>
    <div>
        <Chart :cdata="cdata" />
    </div>
</template>

<script>
import Chart from "./chart.vue";
export default {
    data() {
        return {
            cdata: {
                category: [
                    "2019年报",
                    "2020年报",
                    "2021年报",
                    "2022年报",
                    "2023年报",
                    "2024年报",
                ],
                tax_one: [100, 150, 220, 310, 430, 570],
                tax_two:  [120, 180, 250, 340, 460, 600],
                tax_three: [130, 190, 270, 360, 480, 620],
                tax_four:  [140, 200, 290, 380, 500, 640],
                tax_rate: [20, 25, 36.36, 45.16, 61.29, 68.18],
            },
        };
    },
    components: {
        Chart,
    },
    mounted() {
        this.setData();
    },
    methods: {

    },
};
</script>

<style lang="scss" scoped></style>
