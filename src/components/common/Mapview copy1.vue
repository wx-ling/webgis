<template>
    <div>
        <div id="mapview" style="height: 1000px;"></div>
    </div>
</template>

<script>
import { loadModules } from 'esri-loader';

    const options = {
        url: "https://js.arcgis.com/4.22/init.js/",
        css: "https://js.arcgis.com/4.22/esri/themes/light/main.css",
    };

    export default {
        name: 'Mapview',
        components: {},
        mounted() {
            this.$nextTick(() => {
                this.createMapViwe();
            });
            
        },
        methods: {
            async _createMapViwe() {
                const [Map,Mapview] = await loadModules(
                    ['esri/Map','esri/views/MapView'],
                    options
                );
                
                const map = new Map({
                    basemap: 'topo-vector',
                });
                
                const view = new Mapview({
                    container: 'mapview',
                    map: map,
                    zoom: 10,
                });
                console.log(view);
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