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
                        @select="handleMenuSelect"
                >
                    <el-scrollbar style="height:100%">
                        <el-menu-item v-for="menu in menus"
                                      :index="menu.name"
                                      :key="menu.name"
                        >
                            <i :class="menu.classes"></i>
                            <span slot="title">
                                {{ menu.title }}
                            </span>
                        </el-menu-item>
                    </el-scrollbar>
                </el-menu>
            </el-aside>
            <el-container>
                <el-main>
                    <el-tabs v-model="editableTabsValue" type="card" closable @tab-remove="removeTab">
                        <el-tab-pane
                                v-for="item in editableTabs"
                                :key="item.name"
                                :label="item.title"
                                :name="item.name"
                                :route="item.route"
                        >
                            <router-view></router-view>
                        </el-tab-pane>
                    </el-tabs>
                </el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
    // import HelloWorld from './components/HelloWorld.vue'

    const MENU_NAME_FROM = {title:'表单', name:'form', classes:'el-icon-menu', route: '/form'};
    const MENU_NAME_TEST = {title:'表格', name:'table', classes:'el-icon-s-operation', route:'/table'};

    export default {
        name: 'App',
        data: function () {
            return {
                menus: [
                    MENU_NAME_FROM, MENU_NAME_TEST,
                ],


                // 当前正被选择的 tab(menu) 的 name
                editableTabsValue: '',
                // 当前被选中的 tab(menu)
                editableTabs: [],
            }
        },
        components: {
            // HelloWorld
        },
        methods: {
            /**
             * 监听左侧菜单栏的选择
             * @param key - 被选中的菜单的 key
             */
            handleMenuSelect: function (key) {
                if (this.editableTabsValue !== key) {
                    this.$router.push(this.getMenuRecord(key).route);
                    this.addTab(key);
                }
            },
            /**
             * 获取一个菜单的中文标识
             * @param menuKey - 菜单的英文标识
             */
            getMenuRecord(menuKey) {
                for (let item of this.menus) {
                    if (menuKey === item.name) {
                        return item;
                    }
                }
            },
            /**
             * 通过路由获取一个菜单
             * @param route - 路由
             */
            getMenuRecordByRoute(route) {
                for (let item of this.menus) {
                    if (route === item.route) {
                        return item;
                    }
                }
            },
            /**
             * 一个 tab 是否被添加过，如果是，则打开，否则新建
             * @param menuKey - menu 的 key
             * @return boolean - true: 被打开了，false: 未被打开
             */
            isTabAdded(menuKey) {
                for (let openedMenu of this.editableTabs) {
                    if (openedMenu.name === menuKey) {
                        return true;
                    }
                }
                return false;
            },
            /**
             * 添加一个 tab
             */
            addTab(menuKey) {
                if (!this.isTabAdded(menuKey)) {
                    this.editableTabs.push(this.getMenuRecord(menuKey));
                }
                this.editableTabsValue = menuKey;
            },
            /**
             * 删除一个 tab
             * @param targetName - 需要删除的 menu 的 name
             */
            removeTab(targetName) {
                let tabs = this.editableTabs;
                let activeName = this.editableTabsValue;
                if (activeName === targetName) {
                    tabs.forEach((tab, index) => {
                        if (tab.name === targetName) {
                            let nextTab = tabs[index + 1] || tabs[index - 1];
                            if (nextTab) {
                                activeName = nextTab.name;
                            }
                        }
                    });
                }
                this.editableTabsValue = activeName;
                this.editableTabs = tabs.filter(tab => tab.name !== targetName);
            }
        },
        mounted() {
            let currentRoute = this.$router.currentRoute;
            if (currentRoute.path !== '/') {
                this.addTab(this.getMenuRecordByRoute(currentRoute.path).name);
            }
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
