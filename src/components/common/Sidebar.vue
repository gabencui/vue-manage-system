<template>
    <div class="sidebar">
        <el-menu :default-active="onRoutes" class="el-menu-vertical-demo" theme="dark" unique-opened router>
            <!--<p>{{ onRoutes }}</p>-->
        <!--<el-menu :default-active="onRoutes" class="el-menu-vertical-demo" theme="dark" router>-->
            <template v-for="item in items">
                <template v-if="item.subs">
                    <el-submenu :index="item.index">
                        <template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>
                        <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index">{{ subItem.title }}
                        </el-menu-item>
                    </el-submenu>
                </template>
                <template v-else>
                    <el-menu-item :index="item.index">
                        <i :class="item.icon"></i>{{ item.title }}
                    </el-menu-item>
                </template>
            </template>
        </el-menu>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                items: [
                    {
                        icon: 'el-icon-setting',
                        index: '/readme',
                        title: '自述'
                    },
                    {
                        icon: 'el-icon-menu',
                        index: '2',
                        title: '表格',
                        subs: [
                            {
                                index: '/basetable/pek1',
                                title: '北京1区'
                            },
                            {
                                index: '/basetable/pek2',
                                title: '北京2区'
                            },
                            {
                                index: '/basetable/pek3a',
                                title: '北京3区'
                            },
                            {
                                index: '/basetable/ap1',
                                title: '亚太1区'
                            },
//                            {
//                                index: 'basetable',
//                                title: '基础表格'
//                            },
//                            {
//                                index: 'vuetable',
//                                title: 'Vue表格组件'
//                            }
                        ]
                    },
                    {
                        icon: 'el-icon-date',
                        index: '3',
                        title: '表单',
                        subs: [
                            {
                                index: '/baseform',
                                title: '基本表单'
                            },
                            {
                                index: '/vueeditor',
                                title: '编辑器'
                            },
                            {
                                index: '/markdown',
                                title: 'markdown'
                            },
                            {
                                index: '/upload',
                                title: '文件上传'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-star-on',
                        index: '/basecharts',
                        title: '图表'
                    },
                    {
                        icon: 'el-icon-upload2',
                        index: '/drag',
                        title: '拖拽'
                    }
                ]
            }
        },

        computed:{
            onRoutes(){
//                console.log(this.$route.path);
                return this.$route.path.replace('/','');
            }
        }
    }
</script>

<style scoped>
    .sidebar{
        display: block;
        position: absolute;
        width: 250px;
        left: 0;
        top: 70px;
        bottom:0;
        background: #2E363F;
    }
    .sidebar > ul {
        height:100%;
    }
</style>
