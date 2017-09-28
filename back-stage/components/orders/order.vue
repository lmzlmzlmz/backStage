<template>
  <div class="order">
    <order-excel></order-excel>
    <order-conditions></order-conditions>
    <order-list></order-list>
    <el-pagination
     @size-change="handleSizeChange"
     @current-change="handleCurrentChange" 
     :current-page="currentPage4" 
     :page-sizes="[10,50]" 
     :page-size="100" 
     :total="400" 
     layout="total, sizes, prev, pager, next, jumper">
     </el-pagination>
   </div>
</template>
<script>
import orderExcel from './orderExcel.vue'
import orderConditions from './orderConditions.vue'
import orderList from './orderList.vue'
import orderDialog from './orderDialog.vue'
export default {
  data () {
    return {
      statNum: '',
      currentPage4: 1
    }
  },
  components: {
    orderExcel,
    orderConditions,
    orderList,
    orderDialog
  },
  methods: {
    handleSizeChange (val) {
      console.log(val)
    },
    handleCurrentChange (val) {
      console.log(val)
    }
  }
}
</script>
<style scoped>
  .order{
      padding: 20px;
      width: 100%;
  }
  .search{
      width: 100%;
      height: 133px;
      margin-bottom: 25px;
  }
  .search>div{
      float: left;
      margin-right: 10px;
      margin-top: 25px;
  }
  .order-table{
      width: 100%;
      height: auto;
      margin-top: 20px;
  }
  .cell{
      text-align: center;
  }
  .el-table{
      margin-top: 25px;
  }
  .page{
      width: 600px;
      height: 50px;
      margin: 20px auto;
  }
  .page>*{
      float: left
  }
  .total{
      font-size: 14px;
      line-height: 33px;
      padding-left: 8px;
  }
  .el-pagination__jump{
      font-size: 14px;
      line-height: 30px;
  }
</style>
