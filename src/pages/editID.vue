<template>
    <div class="relative-wrap">
        <div class="relative">
            <div class="msg-box">
                <h3 class="msg-setting-box">
                    账号资料
                    <backAndRefresh/>
                </h3>
                <form action="" class="clearfix">
                    <div class="arrangement lineHeight">
                        <span id="msgtitle">账号</span>
                        <el-input v-model="userInfo.account"></el-input>
                    </div>
                    <div class="arrangement">
                        <span id="synopsis">手机</span>
                        <el-input v-model="userInfo.phone"></el-input>
                    </div>
                    <div class="arrangement">
                        <span id="coverImg">邮箱</span>
                        <el-input v-model="userInfo.email"></el-input>
                    </div>
                    <div class="arrangement">
                        <span id="synopsis">姓名/昵称</span>
                        <el-input v-model="userInfo.name"></el-input>
                    </div>
                    <div class="arrangement">
                        <span id="coverImg">组织/公司</span>
                        <el-input v-model="userInfo.company"></el-input>
                    </div>
                    <div class="arrangement ">
                        <span>地区</span>
                        <el-cascader size="small" :options="options" v-model="userInfo.area" expand-trigger="hover" style="width:22%;margin-left:10px">
                        </el-cascader>
                    </div>
                    <div class="arrangement submitBox">
                        <el-button type="primary" @click='save'>提交</el-button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import BackAndRefresh from 'components/BackAndRefresh'
import { regionData } from 'element-china-area-data'
import { mapState } from 'vuex';

export default {
    name: 'msg',
    data() {
        return {
            options: regionData,
            userInfo: Object.assign({},this.$store.state.userInfo)
        }
    },
    methods: {
        save() {
            this.$store.dispatch('saveInfo',this.userInfo)
        }
    },
    computed: mapState([

        // 'account',
        // 'phone',
        // 'company',
        // 'area',
        // 'name',
        // 'email',
    ]),
    components: {
        BackAndRefresh
    }
}

</script>

<style scoped>
* {
    text-align: left;
}

i {
    vertical-align: middle;
    font-size: 15px
}

input {
    height: 36px;
}

.msg-box {
    padding: 15px;
}

input,
textarea {
    color: #555;
}

.msg-setting-box {
    border-bottom: 1px solid #ccc;
    line-height: 28px;
    padding-bottom: 4px;
    margin-bottom: 15px;
}

.moreaction {
    float: right;
    font-size: 16px;
}

.clearfix {
    clear: both;
}

.lineHeight {
    line-height: 44px;
}

.arrangement {
    padding: 10px 0;
}

.arrangement span {
    width: 100px;
    text-align: right;
    display: inline-block;
    font-size: 14px;
    padding-right: 10px;
}

.arrangement .el-input {
    padding: 10px;
    width: 22%;
}

.synopsis {
    width: 60%;
    height: 60px;
}

.borde {
    border: 1px solid #ccc;
    border-radius: 4px;
}

.arrangement img {
    margin: 0 10px;
}

.submitBox {
    text-align: center;
}

.arrangement .el-checkbox {
    margin-left: 10px;
}

.el-button {
    padding: 10px 50px;
}
</style>
