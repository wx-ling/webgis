<template>
    <div id="app">
        <el-container class="app-out-pannel">
            <el-header class="sys-header">系统标题</el-header>
            <el-container class="app-conten-pannel">
                <el-aside width="200px" class="sys-menu">左侧菜单</el-aside>
                <el-main>地图区域</el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
    export default {
        name: 'App'
    }
</script>

<style>
    html,
    body,
    #app {
        position: relative;
        width: 100%;
        height: 100%;
        margin: 0;
    }
    .app-out-pannel,
    .app-conten-pannel {
        height: 100%;
    }
    .sys-header {
        background-color: #409EFF;
        line-height: 60px;
        color: #fff;
        font-size: 20px;
    }
    .sys-menu {
        background-color: #C0C4CC;
    }
</style>