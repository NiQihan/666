<template>
    <el-form ref="form" :model="form_data" label-width="120px">
        <el-form-item label="活动名称">
            <el-input placeholder="活动名称" v-model="form_data.name" clearable/>
        </el-form-item>

        <el-form-item label="活动详情">
            <el-input type="textarea" autosize placeholder="请输入内容" v-model="form_data.detail"/>
        </el-form-item>


        <el-form-item label="活动时间">
            <el-date-picker v-model="form_data.date_range" type="daterange" range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期"/>
        </el-form-item>

        <el-form-item label="抢票开始时间">
            <el-date-picker v-model="form_data.starting_date" type="date" placeholder="选择日期"/>
        </el-form-item>

        <el-form-item label="总票数">
            <el-input placeholder="请输入内容" v-model="form_data.amount" clearable/>
        </el-form-item>

        <el-form-item label="抢票成功短信">
            <el-switch v-model="form_data.send_message"/>
            <el-input type="textarea" autosize placeholder="请输入内容" v-model="form_data.message_content"/>
        </el-form-item>
  
        <el-form-item>
            <el-button type="primary" @click="submit">立即创建</el-button>
            <el-button @click="reset">重置</el-button>
        </el-form-item>
</el-form>    
</template>

<script>
 /* eslint-disable */
export default {
    data: () => ({

        form_data: {
            name: '',
            detail: '',
            date_range: '',
            starting_date: '',
            amount: 0,
            send_message: true,
            message_content: '',
        },
    }),

    methods: {
        submit () {
            console.dir('submit');
        },

        reset(form_name) {
            this.$refs.form.resetFields();
        }
    }
}
</script>

<style scoped>

</style>

