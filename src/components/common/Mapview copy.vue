<template>
    <div>
        <div id="mapview" style="height: 1000px;"></div>
    </div>
</template>

<script>
import { loadModules,loadCss,setDefaultOptions } from 'esri-loader';

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
                console.log(111);
                setDefaultOptions({url: 'https://js.arcgis.com/4.20/init.js'})
                loadCss('https://js.arcgis.com/4.20/esri/themes/light/main.css')
                loadModules([
                    "esri/Map",
                    "esri/views/MapView",
                    "esri/layers/MapImageLayer",
                    "esri/tasks/QueryTask",
                    "esri/tasks/support/Query"
                    ], { css: true }).then(([Map, MapView, MapImageLayer, QueryTask, Query]) => {
                        // this.layer = new MapImageLayer({
                        //     url: "http://localhost:6080/arcgis/rest/services//SampleWorldCities/MapServer"
                        // });
                        this.map = new Map({
                            basemap: "streets-vector"
                        });
                        const view = new MapView({
                            map: this.map,
                            container: 'mapview',
                        });
                    })
            }
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