<template>
    <el-form ref="form" :model="form_data" label-width="120px">
        <el-form-item label="活动名称">
            <el-input placeholder="活动名称" v-model="form_data.name" clearable style="width:700px;"/>
        </el-form-item>

        <el-form-item label="活动详情">
            <el-input type="textarea" autosize placeholder="请输入内容" v-model="form_data.detail" style="width:700px;"/>
        </el-form-item>


        <el-form-item label="活动时间">
            <el-date-picker v-model="form_data.date_range" type="daterange" range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期"/>
        </el-form-item>

        <el-form-item label="抢票开始时间">
            <el-date-picker v-model="form_data.starting_date" type="date" placeholder="选择日期"/>
        </el-form-item>
        <el-form-item label="总票数">
            <el-input-number v-model="form_data.num1" @change="handleChange" :min="1" label="描述文字"></el-input-number>
        </el-form-item>

        <el-form-item label="抢票成功短信">
            <div style="display:block;">
            <el-switch v-model="form_data.send_message" style="display:block margin:20px,0;"/>
            </div>
            <el-input v-model="form_data.ticket_name" placeholder="请输入门票名称" style=" width:700px" clearable></el-input>
            <el-input v-model="form_data.ticket_date" placeholder="请输入时间" style="width:700px;" clearable ></el-input>
            <el-input v-model="form_data.ticket_place" placeholder="请输入地点" style="width:700px;" clearable></el-input>
            <el-input :placeholder="`【西电学生会】您好，恭喜您获得${form_data.ticket_name1}一张。请于${form_data.ticket_date1}凭短信与本人一卡通前往${form_data.ticket_place1}}领取您的门票。（感谢西电为之工作室对本次抢票提供的技术支持）`" v-model="input1" :disabled="true" type="textarea" :rows="4" style="width:700px;"></el-input>
        </el-form-item>
  
        <el-form-item>
            <el-button type="primary" @click="submit">创建活动</el-button>
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
            num1:'',
            ticket_name:'',
            ticket_name1:'{{门票名称}}',
            ticket_date:'',
            ticket_date1:'{{时间}}',
            ticket_place:'',
            ticket_place1:'{{地点}}',
            holder:'',
        },
    }),
    
    methods: {
        submit () {
            console.dir('submit');
        },

        reset(form_name) {
            this.$refs.form.resetFields();
        },
        handleChange(value) {
            console.log(value);
        }
    },
    watch: {
      'form_data.ticket_name'(val) {
        this.form_data.ticket_name1 = this.form_data.ticket_name;
      },
      'form_data.ticket_date'(val) {
        this.form_data.ticket_date1 = this.form_data.ticket_date;
      },
      'form_data.ticket_place'(val) {
        this.form_data.ticket_place1 = this.form_data.ticket_place;
      }
    }
}
</script>

<style scoped>

</style>

