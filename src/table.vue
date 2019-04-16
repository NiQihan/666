<template>
<!-- 历史活动表格 -->
    <el-table :data="history_data" style="width: 100%" stripe>

      <!-- 活动名称 -->
      <el-table-column prop="name" label="活动名称" width="400">
        <template slot-scope="scope">
          <span style="margin-left: 10px">{{ scope.row.name + "&nbsp;&nbsp;&nbsp;"}}</span>
          <el-tag type="success" v-if="scope.row.state === 'pending'">进行中</el-tag>
          <el-tag type="danger" v-else-if="scope.row.state === 'end'">已结束</el-tag>
      </template>
      </el-table-column>

      <!-- 抢票开始时间 -->
      <el-table-column prop="date" label="抢票开始时间" width="200" center></el-table-column>

      <!-- 活动人数 -->
      <el-table-column prop="amount" label="活动人数" width="120"></el-table-column> 

      <!-- 操作   -->
      <el-table-column label="操作">
        <template slot-scope="scope">
            <el-button size="mini" @click="dialogFormVisible = true,handleDelete(scope.$index, scope.row)">信息编辑</el-button>
            <!-- <el-dialog title="信息编辑" :visible.sync="dialogFormVisible">
              <el-form :model="form" >
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
  <div slot="footer" class="dialog-footer">
    <el-button @click="dialogFormVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
  </div>
</el-dialog> -->

            <el-button type="link" size="mini">分享链接</el-button>
            <el-button type="QRcode" size="mini">导出数据</el-button>
        </template>
      </el-table-column>  

      <!-- 反馈删除操作 -->
      <el-table-column label="">
        <template slot-scope="scope">
          <el-badge :value="12" class="item">
          <el-button
          size="mini"
          type="warning"
          @click="handleEdit(scope.$index, scope.row)">反馈</el-button>
          </el-badge> 
        <el-button type="danger" size="small" @click="open2">删除活动</el-button>
        </template>
      </el-table-column>  
    </el-table>
  </template>

  <script>
  /* eslint-disable */
    export default {
      data() {
        return {
          history_data: [
              { name: '埃米尔韩中国行', state: 'pending', date: '2019.11.11', amount: 1111,visible2: false},
              { name: '活动2', state: 'pending', date: '2019.11.11', amount: 1111 },
              { name: '活动3', state: 'end', date: '2019.11.11', amount: 1111 },
              { name: '活动4', state: 'pending', date: '2019.11.11', amount: 1111 },
          ]
        }
      },

      methods: {
          show(s) {
              console.dir(s.row.state);
          },
          deleteRow(index, rows) {
              rows.splice(index, 1);
          },
          open2() {
        this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.$message({
            type: 'success',
            message: '删除成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          });          
        });
      },
      }
    }
  </script>
<style>
.item{
  margin-top: 10px;
  margin-right: 40px;
}


</style>
