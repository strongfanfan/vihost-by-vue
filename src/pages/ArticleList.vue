<template>
    <div class="relative-wrap">
        <div class="relative">
            <div class="msg-box">
                <h3 class="msg-setting-box">
                    文章列表
                    <div class="moreaction">
                        <router-link to='/AddArticle'>
                            <i class="el-icon-plus"></i>添加文章
                        </router-link>
                        <BackAndRefresh/>
                    </div>
                </h3>
                <div class="content-itemlist">
                    <div class="presentation">列表</div>
                    <el-table :data="tableData" border style="width: 100%">
                        <el-table-column prop="id" label="ID" width="80px"></el-table-column>
                        <el-table-column prop="title" label="分类名称"></el-table-column>
                        <el-table-column prop="style" label="类型"></el-table-column>
                        <el-table-column prop="cover" label="封面" width="120px"></el-table-column>
                        <el-table-column prop="sort" label="排序" width="70px"></el-table-column>
                        <el-table-column prop="praise" label="点赞"></el-table-column>
                        <el-table-column prop="comment" label="评论"></el-table-column>
                        <el-table-column prop="source" label="文章来源"></el-table-column>
                        <el-table-column prop="pageviews" label="浏览量"></el-table-column>
                        <el-table-column prop="editDate" label="最后编辑时间" width="150px"></el-table-column>
                        <el-table-column label="操作" width="200px">
                            <template scope="scope">
                                <el-button type="text" size="small" icon="edit">编辑</el-button>
                                <el-button type="text" size="small" icon="delete2">删除</el-button>
                                <el-button type="text" size="small">链接地址</el-button>
                            </template>
                        </el-table-column>
                    </el-table>
                </div>
                <div class="numberOf">共 <span>1</span> 条数据</div>
                <div style="clear:both;"></div>
            </div>
        </div>
    </div>
</template>

<script>
import BackAndRefresh from 'components/BackAndRefresh'
export default {
    data() {
        return {
            tableData: [{
                id: '2016-05-02',
                title: 'sd',
                style: '王小虎',
                cover: 'dsf',
                sort: '10',
                praise: 'sdgtr',
                comment: 'sdgr',
                source: 'hgf',
                pageviews: '图文',
                editDate: '17-4-26 12:45:25',
            }]
        }
    },
    components: { 
        BackAndRefresh
    },
}
</script>

<style scoped>
* {
    text-align: left;
}

.msg-setting-box {
    border-bottom: 1px solid #ccc;
    line-height: 28px;
    padding-bottom: 4px;
    margin-bottom: 15px;
}

.msg-box {
    padding: 15px;
}

.moreaction {
    float: right;
    font-size: 16px;
}

.presentation {
    width: 60px;
    height: 40px;
    line-height: 40px;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    border: 1px solid #ddd;
    text-align: center;
    border-bottom: 1px solid #fff;
    z-index: 1;
    position: relative;
    top: 1px;
}

.el-table_1_column_11 .el-button--text {
    color: #1f2d3d
}

.el-table_1_column_11 .el-button--text:hover {
    color: #00aaef
}

.numberOf {
    float: right;
    width: 100px;
    padding: 6px 12px;
    border: 1px solid #ccc;
    text-align: center;
    margin-top: 20px;
    color: #337ab7;
    border-radius: 4px;
}

.numberOf:hover {
    z-index: 3;
    color: #23527c;
    background-color: #eee;
    border-color: #ddd;
}
</style>