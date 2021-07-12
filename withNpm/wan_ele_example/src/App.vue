<template>
    <div id="app">
        <!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
        <el-container>
            <el-aside width="200px">
                <el-menu
                        default-active="2"
                        class="el-menu-vertical-demo"
                        background-color="#545c64"
                        text-color="#fff"
                        active-text-color="#ffd04b"
                        style="width: 200px; position: absolute; height: 100%;"
                >
                    <el-scrollbar style="height:100%">
                        <el-submenu index="1">
                            <template slot="title">
                                <i class="el-icon-location"></i>
                                <span>导航一</span>
                            </template>
                            <el-menu-item-group>
                                <template slot="title">分组一</template>
                                <el-menu-item index="1-1">选项1</el-menu-item>
                                <el-menu-item index="1-2">选项2</el-menu-item>
                            </el-menu-item-group>
                            <el-menu-item-group title="分组2">
                                <el-menu-item index="1-3">选项3</el-menu-item>
                            </el-menu-item-group>
                            <el-submenu index="1-4">
                                <template slot="title">选项4</template>
                                <el-menu-item index="1-4-1">选项1</el-menu-item>
                            </el-submenu>
                        </el-submenu>
                        <el-menu-item index="2">
                            <i class="el-icon-menu"></i>
                            <span slot="title">导航二</span>
                        </el-menu-item>
                        <el-menu-item index="3" disabled>
                            <i class="el-icon-document"></i>
                            <span slot="title">导航三</span>
                        </el-menu-item>
                        <el-menu-item index="4">
                            <i class="el-icon-setting"></i>
                            <span slot="title">导航四</span>
                        </el-menu-item>
                        <el-submenu index="5">
                            <template slot="title">
                                <i class="el-icon-location"></i>
                                <span>导航一</span>
                            </template>
                            <el-menu-item-group>
                                <template slot="title">分组一</template>
                                <el-menu-item index="5-1">选项1</el-menu-item>
                                <el-menu-item index="5-2">选项2</el-menu-item>
                            </el-menu-item-group>
                            <el-menu-item-group title="分组2">
                                <el-menu-item index="5-3">选项3</el-menu-item>
                            </el-menu-item-group>
                            <el-submenu index="5-4">
                                <template slot="title">选项4</template>
                                <el-menu-item index="5-4-1">选项1</el-menu-item>
                            </el-submenu>
                        </el-submenu>
                        <el-submenu index="5">
                            <template slot="title">
                                <i class="el-icon-location"></i>
                                <span>导航一</span>
                            </template>
                            <el-menu-item-group>
                                <template slot="title">分组一</template>
                                <el-menu-item index="5-1">选项1</el-menu-item>
                                <el-menu-item index="5-2">选项2</el-menu-item>
                            </el-menu-item-group>
                            <el-menu-item-group title="分组2">
                                <el-menu-item index="5-3">选项3</el-menu-item>
                            </el-menu-item-group>
                            <el-submenu index="5-4">
                                <template slot="title">选项4</template>
                                <el-menu-item index="5-4-1">选项1</el-menu-item>
                            </el-submenu>
                        </el-submenu>
                        <el-submenu index="5">
                            <template slot="title">
                                <i class="el-icon-location"></i>
                                <span>导航一</span>
                            </template>
                            <el-menu-item-group>
                                <template slot="title">分组一</template>
                                <el-menu-item index="5-1">选项1</el-menu-item>
                                <el-menu-item index="5-2">选项2</el-menu-item>
                            </el-menu-item-group>
                            <el-menu-item-group title="分组2">
                                <el-menu-item index="5-3">选项3</el-menu-item>
                            </el-menu-item-group>
                            <el-submenu index="5-4">
                                <template slot="title">选项4</template>
                                <el-menu-item index="5-4-1">选项1</el-menu-item>
                            </el-submenu>
                        </el-submenu>
                    </el-scrollbar>
                </el-menu>
            </el-aside>
            <el-container>
                <el-header>Header</el-header>
                <el-main>Main</el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
    // import HelloWorld from './components/HelloWorld.vue'

    export default {
        name: 'App',
        data: function () {
            return {
                //
            }
        },
        components: {
            // HelloWorld
        }
    }
</script>

<style>
    body {
        margin: 0;
    }
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
    }
    .el-aside {
        background-color: #545c64;
        color: #333;
        line-height: 200px;
        position: absolute;
        height: 100%;
        overflow: hidden !important;
    }
    .el-scrollbar__wrap{
        overflow-x:hidden !important;
    }
    .el-header {
        margin-left: 200px;
    }
    .el-main {
        margin-left: 200px;
    }
</style>
