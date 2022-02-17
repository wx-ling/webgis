<template>
    <div>
        <div id="mapview" style="height: 1200px"></div>
    </div>
</template>

<script>
    import { loadCss, setDefaultOptions,loadModules, } from "esri-loader";


    export default {
        name: 'Mapview',
        components: {},

        mounted() {
            this.$nextTick(() => {
                this.createMapViwe();
            });
        },

        methods: {
            createMapViwe() {
                setDefaultOptions({url: 'https://js.arcgis.com/4.20/init.js'})
                loadCss('https://js.arcgis.com/4.20/esri/themes/light/main.css')
                loadModules([
                    'esri/Map',
                    "esri/views/MapView",
                    "esri/layers/MapImageLayer",
                    "esri/tasks/QueryTask",
                    "esri/tasks/support/Query"
                    ], { css: true }).then(([Map, MapView, MapImageLayer, QueryTask, Query]) => {
                    // this.layer = new MapImageLayer({
                    //     url: "http://localhost:6080/arcgis/rest/services//SampleWorldCities/MapServer"
                    this.map = new Map({
                        basemap: "streets-vector",
                    });
                    const views = new MapView({
                        map: this.map,
                        container: "mapview",
                    });
                });




        //         this.pointSymbol = {
        //             type: "simple-marker",
        //             style: "circle",
        //             color: "red",
        //             size: 12
        //         };

        //         //要查询的图层
        //         this.searchUrl = "http://localhost:6080/arcgis/rest/services//SampleWorldCities/MapServer";
        //         this.queryTask = new QueryTask({
        //             url: this.searchUrl,
        //         });

        //         //查询条件
        //         this.query = new Query({
        //             outFields: ['*'],
        //             returnGeomety: true,
        //             where: "CITY_NAME =  '$(this.inputData)'",
        //         });

        //     }).catch(eer => {
        //     console.log(eer);
        // });
    }


    // doQuery() {
    //     //执行属性查询
    //     this.queryTask.execute(this.query).then((result) =>{
    //         this.view.graphics.removeAll ();
    //         if(result.features.length > 0) {
    //             let features = result.features.map((feature) =>{
    //                 features.symbol = this.pointSymbol;
    //                 return features;
    //             });
    //             this.view.graphics.addMany(feature);
    //             this.view.goTo(feature);
    //         }
    //     })
    // },
    }
    };
</script>

<style>
    #Mapview {
        position: relative;
        height: 100%;
        width: 100%;
    }
</style>