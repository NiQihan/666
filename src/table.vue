<template>
    <el-table :data="history_data" style="width: 100%" stripe>
      <el-table-column prop="name" label="活动名称"></el-table-column>
      <el-table-column label="活动状态">
        <template slot-scope="scope">
            <el-tag type="success" v-if="scope.row.state === 'pending'">进行中</el-tag>
            <el-tag type="danger" v-else-if="scope.row.state === 'end'">已结束</el-tag>
            <el-tag type="info" v-else>其他</el-tag>
        </template>
      </el-table-column>
      <el-table-column prop="date" label="结束日期"></el-table-column>
      <el-table-column prop="amount" label="活动人数"></el-table-column>    
      <el-table-column label="操作">
        <template slot-scope="scope">
            <el-button @click="show(scope)" size="mini">信息编辑</el-button>
            <el-button type="danger" size="mini">删除</el-button>
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
              { name: '活动1', state: 'pending', date: '2019.11.11', amount: 1111 },
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