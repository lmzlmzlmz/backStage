<template>
  <div class="order-list">
      <el-table :data="orderList" style="width:100%">
        <el-table-column align="center" v-for="(value,key) in orders" :width="value[1]" :label="value[0]" :prop="key" :key="key"></el-table-column>
        <el-table-column label="客服操作" width="160" align="center">
        <template scope="scope">
            <el-button
            size="small" @click="bussis('service', scope.$index, orderList[scope.$index])">编辑</el-button>
            <el-button
            size="small"
            type="danger">删除</el-button>
        </template>
        </el-table-column>
        <el-table-column label="商家操作" width="160" align="center">
        <template scope="scope">
            <el-button
            size="small" @click="bussis('shop')">编辑</el-button>
            <el-button
            size="small"
            type="danger">删除</el-button>
        </template>
        </el-table-column>
    </el-table>
    <el-dialog
    title="编辑"
    :visible.sync="dialogVisible"
    size="tiny">
    <orderDialog @close="close"></orderDialog>
    </el-dialog>
  </div>
</template>
<script>
import { mapActions, mapGetters, mapState } from 'vuex'
import orderDialog from './orderDialog.vue'
import { Order, tableMain } from 'assets/js/modules.js'
export default {
  computed: mapState({
    editType: ({order}) => order.editType.type,
    obj: ({order}) => order.editType.obj
  }),
  data () {
    return {
      dialogVisible: false,
      status: '',
      orderList: tableMain,
      orders: Order,
      index: 0
    }
  },
  methods: {
    ...mapActions(['orderEditType']),
    bussis (type, value, obj) {
      this.dialogVisible = true
      this.index = value
      this.orderEditType({
        type: type,
        obj: obj
      })
    },
    close (bool, obj) {
      this.orderList[this.index] = obj
      this.dialogVisible = bool
      // console.log(bool)
    }
  },
  components: {
    orderDialog
  }
}
</script>
<style scoped>

</style>

