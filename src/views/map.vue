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
                        // center: [114.704689, 27.802502], // 初始化地图中心点位置
                        center: [  114.640422, 27.799924],
                         mapStyle: "amap://styles/grey", //https://lbs.amap.com/api/javascript-api-v2/guide/map/map-style
                    });
                    // Adding markers
                    const marker1 = new AMap.Marker({
                        position: new AMap.LngLat(114.640422, 27.799924),
                        offset: new AMap.Pixel(-10, -10),
                        icon: "//vdata.amap.com/icons/b18/1/2.png",
                        title: "分宜",
                    });

                    this.map.add(marker1);

                    var path = [
                        new AMap.LngLat( 114.631252, 27.801080), //左上
                        new AMap.LngLat( 114.634475, 27.793911), //左下
                        new AMap.LngLat( 114.635749, 27.794072),
                        new AMap.LngLat( 114.636777, 27.792233),
                        new AMap.LngLat( 114.637763, 27.792689),
                        new AMap.LngLat( 114.638568, 27.791575),
                        new AMap.LngLat( 114.640191,27.793978),
                        new AMap.LngLat( 114.642224,27.794542),
                        new AMap.LngLat( 114.642100,27.795628),
                        new AMap.LngLat( 114.656561, 27.798589), //右边下
                        new AMap.LngLat(114.656420, 27.805451), //右边上              
                    ];

                    var path2 = [
                        new AMap.LngLat(114.618146, 27.791113),
                        new AMap.LngLat(114.618468, 27.790600),
                        new AMap.LngLat(114.618929,  27.790733),
                        new AMap.LngLat(114.619777,  27.790382),

                        new AMap.LngLat( 114.622813,  27.791625),
                        new AMap.LngLat(114.619536, 27.798146),
                        new AMap.LngLat(114.618142,  27.797558),
                        new AMap.LngLat(114.617019,  27.798740),

                    ]

                    var polygon = new AMap.Polygon({
                        path: [path, path2], //路径
                        fillColor: "#fff", //多边形填充颜色
                        strokeWeight: 2, //线条宽度，默认为 2
                        strokeColor: "red", //线条颜色
                    });

                    //多边形 Polygon对象添加到 Map
                    this.map.add(polygon);
                    //将覆盖物调整到合适视野
                    this.map.setFitView([polygon])
                })
                .catch((e) => {
                    console.log(e);
                });
        },
    },
};
</script>
<style lang="scss" scoped>
$box-width: 550px;
$box-height: 430px;

#container {
  padding: 16px;
  margin-left: 10px;
  height: $box-height;
  width: $box-width;
  border-radius: 10px;
  border: 5px solid #0e101f;
}
</style>

