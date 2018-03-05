

<template>
    <div class="admin">
        <el-container class="admin-content">

            <el-aside width="200px">
                <app-aside></app-aside>
            </el-aside>
            <el-container>
                <!-- 公共头部 -->
                <el-header>
                    <app-header></app-header>
                </el-header>
                <!-- 公共左侧 -->
                <el-main>Main</el-main>
            </el-container>
        </el-container>
 
    </div>
</template>

<script>
import Header from './subcom/Header.vue';
import Aside from './subcom/Aside.vue';
export default {
    // 注册子组件
    components: {
        appHeader: Header,
        appAside: Aside
    }
}
</script>

<style scoped lang="less">
.admin{
    height:100%;
    .el-header{
        height:60px;
    }
    .admin-content{
        height:100%;
    }
}

.el-header,
.el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
}

.el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
}

.el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
}

body>.el-container {
    margin-bottom: 40px;
}

.el-container:nth-child(6) .el-aside {
    line-height: 260px;
}

</style>