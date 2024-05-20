<template>
    <div id="container"></div>
</template>
<script>
import AMapLoader from "@amap/amap-jsapi-loader";

export default {
    name: "map-view",
    mounted() {
        this.initAMap();
    },
    unmounted() {
        this.map?.destroy();
    },
    methods: {
        initAMap() {
            window._AMapSecurityConfig = {
                securityJsCode: "bd11b18758595bbb38b58b855058bdf5",
            };
            AMapLoader.load({
                key: "8d3da3d1ee0b5c16925328e4c9996123", // 申请好的Web端开发者Key，首次调用 load 时必填
                version: "2.0", // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
                plugins: ["AMap.Scale"], //需要使用的的插件列表，如比例尺'AMap.Scale'，支持添加多个如：['...','...']
            })
                .then((AMap) => {

                    //创建路网图层
                    // var roadNet = new AMap.TileLayer.RoadNet();

                    this.map = new AMap.Map("container", {
                        // layers: [roadNet],
                        // 设置地图容器id
                        viewMode: "2D", // 是否为3D地图模式
                        zoom: 17, // 初始化地图级别
                        center: [114.704689, 27.802502], // 初始化地图中心点位置
                        
                        mapStyle: "amap://styles/grey",
                    });
                    // Adding markers
                    const marker1 = new AMap.Marker({
                        position: new AMap.LngLat(114.704689, 27.802502),
                        offset: new AMap.Pixel(-10, -10),
                        icon: "//vdata.amap.com/icons/b18/1/2.png",
                        title: "分宜",
                    });
                    this.map.add(marker1);

                    


                })
                .catch((e) => {
                    console.log(e);
                });
        },
    },
};
</script>
<style lang="scss" scoped>
$box-height: 410px;
$box-width: 500px;

#container {
    padding: 16px;
    margin-left: 10px;
    height: $box-height;
    width: $box-width;
    border-radius: 10px;
    border: 5px solid #0e101f;
}
</style>
