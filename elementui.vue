<template>
  <div class="test">
    <h2>{{msg}}</h2>
    <el-table :data="tableData"
              ref="table0"
              style="width: 100%;margin-bottom: 20px;"
              row-key="id"
              border>
      <!-- 展开行内容 -->
      <el-table-column type="expand"
                       width="1">
        <template>
          <el-table :data="tableData1"
                    style="width: 100%">
            <el-table-column prop="date"
                             label="日期"
                             width="180">
            </el-table-column>
            <el-table-column prop="name"
                             label="姓名"
                             width="180">
            </el-table-column>
            <el-table-column prop="address"
                             label="地址">
            </el-table-column>
          </el-table>
        </template>
      </el-table-column>
      <!-- end -->

      <el-table-column prop="date"
                       label="日期"
                       sortable
                       width="180">
      </el-table-column>
      <el-table-column label="姓名"
                       width="180">
        <template slot-scope="scope">
          <div @click="handleClik(scope.row)">{{scope.row.name}}</div>
        </template>
      </el-table-column>
      <el-table-column prop="address"
                       label="地址">
      </el-table-column>
    </el-table>
    <div>
      <button @click="aa">click</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'testWorld',
  data () {
    return {
      msg: 'msgggggg',
      appIsShow: false,
      getRowKeys (row) {
        return row.id;
      },
      expands: [],
      tableData: [
        {
          id: 1,
          keyId: 1,
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          children: [{
            id: 33,
            keyId: 1,
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            id: 32,
            keyId: 1,
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }]
        },
        {
          id: 2,
          keyId: 2,
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄',
          children: [{
            id: 35,
            keyId: 2,
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            id: 36,
            keyId: 2,
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }]
        },
      ],
      tableData1: [
        {
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄'
        }
      ]
    }
  },
  methods: {
    aa () {
      let $table = this.$refs.table0;
      $table.toggleRowExpansion(this.tableData[0])
    },
    toggleRowExpansion (row) {
      this.expands = [];
      this.expands.push(row.id);
    },
    handleClik (row) {
      console.log('row ', row)
      let $table = this.$refs.table0;
      // this.tableData.map((item) => {
      //   if (row.id != item.id) {
      //     $table.toggleRowExpansion(item, false)
      //   } else {
      //     $table.toggleRowExpansion(row)
      //   }
      // })
      $table.toggleRowExpansion(row)
    }
  },
  created () {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="less">
</style>
