<template>
    <div class="wrap">
        <!--<el-menu theme="dark" :default-active="activeIndex" mode="horizontal" menu-trigger='click' class="h-nav">
                        <router-link to='/index'>
                            <el-menu-item index="1"><i class='main-icon'></i>管理平台</el-menu-item>
                        </router-link>
                        <el-submenu index="2">
                            <span slot="title">产品与服务</span>
                            <el-menu-item index="2-1">选项1</el-menu-item>
                            <el-menu-item index="2-2">选项2</el-menu-item>
                            <el-menu-item index="2-3">选项3</el-menu-item>
                        </el-submenu>
                        <el-menu-item index="3">公积金管理局</el-menu-item>
                    </el-menu>-->
        <el-col :span='3' class="v-nav">
            <el-menu theme='dark' mode='vertical' menu-trigger='click' :unique-opened="true">
                <router-link to='/'>
                    <el-menu-item index="v-1" class=''>后台首页</el-menu-item>
                </router-link>
                <router-link to='/depart'>
                    <el-menu-item index="v-2" class=''>首页管理</el-menu-item>
                </router-link>
                <router-link to='/qr'>
                    <el-menu-item index='v-3' class="icon-wrap">二维码
                        <i class='el-icon-picture icon-item'></i>
                    </el-menu-item>
                </router-link>
                <el-submenu index="v-4">
                    <span slot="title">服务窗</span>
                    <router-link to='/serviceWindow/menu'>
                        <el-menu-item index="v-4-1" class='menu-mixin'>菜单管理</el-menu-item>
                    </router-link>
                    <router-link to='/serviceWindow/reply'>
                        <el-menu-item index="v-4-2" class='menu-mixin'>回复管理</el-menu-item>
                    </router-link>
                </el-submenu>
                <el-submenu index="v-5">
                    <span slot="title">用户管理</span>
                    <router-link to='/tagsManagement'>
                        <el-menu-item index="v-5-1" class='menu-mixin'>标签管理</el-menu-item>
                    </router-link>
                    <!--<router-link to='/'>-->
                    <el-menu-item index="v-5-2" class='menu-mixin'>用户列表</el-menu-item>
                    <!--</router-link>-->
                </el-submenu>
                <el-submenu index="v-6">
                    <span slot="title">公告管理</span>
                    <router-link to='/bulletin/list'>
                        <el-menu-item index="v-6-1" class='menu-mixin'>公告列表</el-menu-item>
                    </router-link>
                    <router-link to='/bulletin/addBulletin'>
                        <el-menu-item index="v-6-2" class='menu-mixin'>发布公告</el-menu-item>
                    </router-link>
                </el-submenu>
                <el-submenu index="v-7" class="icon-wrap">
                    <span slot="title">文章管理</span>
                    <router-link to='/article/column'>
                        <el-menu-item index="v-7-1" class='menu-mixin'>文章栏目</el-menu-item>
                    </router-link>
                    <router-link to='/article/list'>
                        <el-menu-item index="v-7-2" class='menu-mixin'>文章列表</el-menu-item>
                    </router-link>
                </el-submenu>
                <el-submenu index="v-8" class="icon-wrap">
                    <span slot="title">入驻部门</span>
                    <router-link to='/settled/list'>
                        <el-menu-item index="v-8-1" class='menu-mixin'>入驻部门列表</el-menu-item>
                    </router-link>
                    <router-link to='/settled/addSettled'>
                        <el-menu-item index="v-8-2" class='menu-mixin'>添加部门入驻</el-menu-item>
                    </router-link>
                </el-submenu>
                <router-link to='/editID'>
                    <el-menu-item index="v-9" class="icon-wrap">修改账号资料</el-menu-item>
                </router-link>
                <router-link to='/departmentAccount'>
                    <el-menu-item index="v-10" class="icon-wrap">部门账号管理</el-menu-item>
                </router-link>
            </el-menu>
    
        </el-col>
        <section class="top-bar  clear-fix">
            <el-breadcrumb separator="/">
                <!--<el-breadcrumb-item :to="{ path: '/index' }">首页</el-breadcrumb-item>-->
                <el-breadcrumb-item v-for="item in routeName" key="item" :to='item.path'>{{ item.name }}</el-breadcrumb-item>
                
            </el-breadcrumb>
            <span class="user">
                <i class='main-icon'></i>
                <el-dropdown>
                    <span class="el-dropdown-link">
                        {{userName}}
                        <i class="el-icon-caret-bottom el-icon-right"></i>
                    </span>
                    <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item>账号设置</el-dropdown-item>
                        <el-dropdown-item>退出</el-dropdown-item>
                    </el-dropdown-menu>
                </el-dropdown>
            </span>
        </section>
        <vue-progress-bar></vue-progress-bar>
        <router-view>
    
        </router-view>
    
    </div>
</template>
<script>
export default {
    beforeMount() {
        this.$Progress.start()
    },
    mounted() {
        this.$Progress.finish()
    },
    data() {
        return {
            activeIndex: '1',
            activeIndex2: '1',
        };
    },
    methods: {
        handleSelect(key, keyPath) {
            console.log(key, keyPath);
        }
    },
    computed: {
        routeName() {
            return this.$route.matched.length===1?null:this.$route.matched
        },
        userName(){
            return  this.$store.state.userInfo.name
        }
    },
    components: {
    },
    watch: {

    }

}
</script>


<style>
html,
body,
#app,
.wrap {
    width: 100%;
    height: 100vh;
    text-align: center;
    overflow: hidden
}

;
* {
    padding: 0;
    margin: 0
}

.menu-mixin {
    background-color: #1D8CE0
}

.menu-mixin:hover {
    background-color: #475669
}

.top-bar {
    background-color: #EFF2F7;
    text-align: left;
    padding: 10px 0;
    margin: 1px 0;
    border-radius: 3px;
}

.user {
    float: right;
    margin-right: 20px
}



/*
.v-nav {
    position: absolute;
    box-sizing: border-box;
    top: 0;
    padding-top: 60px;
    height: 100vh;
    background-color: #324057
}*/

.icon-wrap {
    position: relative
}

.icon-item {
    position: absolute;
    top: 20px;
    right: 10px
}

.wrap {
    background-color: #324057
}

.relative {
    /*position: relative;*/
    left: 12.5%;
    /*width: 87.5%;*/
    min-height: 100vh;
    background-color: #fff
}

.relative-wrap {
    overflow: auto;
    height: 100vh;
    /*height: 100%*/
}

.relative p {
    text-align: left;
    margin: 20px 0 0 20px
}

a {
    text-decoration: none
}

.main-icon {
    background: transparent url('http://oq6scdosy.bkt.clouddn.com/4eyes-2011.png') no-repeat center;
    background-size: cover;
    display: inline-block;
    width: 30px;
    height: 30px;
    vertical-align: -10px;
    margin-right: 10px;
    border-radius: 5px
}
.el-breadcrumb{
    display: inline-block;
    vertical-align: bottom;
    margin-left: 20px
}

.clear-fix {

    overflow: auto
}
.el-tree-node__content:hover .tree-edit{
    opacity: 1!important
}


</style>