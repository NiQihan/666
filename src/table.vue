<template>
    <el-table :data="history_data" style="width: 100%" stripe>
      <el-table-column prop="name" label="活动名称" width="400">
        <template slot-scope="scope">
          <span style="margin-left: 10px">{{ scope.row.name + "&nbsp;&nbsp;&nbsp;"}}</span>
          <el-tag type="success" v-if="scope.row.state === 'pending'">进行中</el-tag>
          <el-tag type="danger" v-else-if="scope.row.state === 'end'">已结束</el-tag>
      </template>
      </el-table-column>
      <el-table-column prop="date" label="抢票开始时间" width="200" center></el-table-column>
      <el-table-column prop="amount" label="活动人数" width="120"></el-table-column>    
      <el-table-column label="操作">
        <template slot-scope="scope">
            <el-button @click="show(scope)" size="mini">信息编辑</el-button>
            <el-button type="link" size="mini">分享链接</el-button>
            <el-button type="QRcode" size="mini">导出数据</el-button>
        </template>
      </el-table-column>  
      <el-table-column label="">
        <template slot-scope="scope">
            <el-button
          size="mini"
          @click="handleEdit(scope.$index, scope.row)">反馈</el-button>
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)">删除</el-button>
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
              { name: '埃米尔韩中国行', state: 'pending', date: '2019.11.11', amount: 1111 },
              { name: '活动2', state: 'pending', date: '2019.11.11', amount: 1111 },
              { name: '活动3', state: 'end', date: '2019.11.11', amount: 1111 },
              { name: '活动4', state: 'pending', date: '2019.11.11', amount: 1111 },
          ]
        }
      },

      methods: {
          show(s) {
              console.dir(s.row.state);
          }
      }
    }
  </script>
 