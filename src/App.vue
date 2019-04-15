<template>
<el-container>
    <el-header class="header" height="50px">
        <div class="title"> 为之抢票系统 </div>
    </el-header>
  
    <el-container>
        <el-aside width="200px">
            <el-menu default-active="1" class="el-menu-vertical-demo" >
                <el-menu-item index="1" @click="page = 'table'">
                    <i class="el-icon-menu"></i>
                    <span slot="title"> 活动列表 </span>
                </el-menu-item>

                <el-menu-item index="2" @click="page = 'create'">
                    <i class="el-icon-setting"></i>
                    <span slot="title"> 新建活动 </span>
                </el-menu-item>
            </el-menu>
        </el-aside>
    
        <el-main class="main-page">
            <history-table v-if="page === 'table'"/>
            <create-activity v-else-if="page === 'create'"/>
        </el-main>
    </el-container>
</el-container>
</template>

<script>
 /* eslint-disable */
import Table from './table.vue'
import Create from './create.vue'

export default {
    components: {
        'history-table': Table,
        'create-activity': Create,
    },

    data: () => ({
        page: 'table',
    }),

    methods: {

    }
}
</script>

<style scoped>
.header {
    background-color: #292B33;
}

.title {
    font-size: 16px; color: white;
    position: absolute;
    left: 10px;
    line-height: 50px;
}

.main-page {
    padding: 20px 40px;
}
</style>
