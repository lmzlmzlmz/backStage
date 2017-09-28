<template>
  <div class="order-search">
      <el-form inline>
        <el-form-item label="活动区域">
            <el-select v-model="conditions.status" placeholder="请选择">
                <el-option
                v-for="(item,key) in orderList"
                :key="key"
                :label="item"
                :value="key">
                </el-option>
            </el-select>
        </el-form-item>
        <el-form-item label="收货城市">
            <el-select v-model="conditions.city" placeholder="请选择">
                <el-option
                v-for="(item,key) in orderUrl"
                :key="key"
                :label="item"
                :value="key">
                </el-option>
            </el-select>
        </el-form-item>
        <el-form-item label="优惠方式">
            <el-select v-model="conditions.favorable" placeholder="请选择">
                <el-option
                v-for="(item,key) in orderFavorable"
                :key="key"
                :label="item"
                :value="key">
                </el-option>
            </el-select>
        </el-form-item>
        <el-form-item label="支付时间">
            <el-date-picker
            v-model="conditions.date"
            type="datetime"
            placeholder="选择日期时间">
            </el-date-picker>
        </el-form-item>
        <el-form-item label="发货商家">
            <el-input v-model="conditions.text" placeholder="请输入内容"></el-input>
        </el-form-item>
        <el-form-item label="关键字">
            <el-input v-model="conditions.text" placeholder="请输入内容"></el-input>
        </el-form-item>
        <el-form-item>
            <el-button type="primary">搜索</el-button>
            <el-button type="primary">重置</el-button>
        </el-form-item>
      </el-form>
  </div>
</template>
<script>
export default {
  data () {
    return {
      conditions: {
        status: '',
        city: '',
        favorable: '',
        payTime: '',
        text: '',
        date: ''
      },
      orderFavorable: {
        1: '免息劵',
        2: '消费劵'
      },
      orderUrl: {
        1: '北京',
        2: '上海',
        3: '广东',
        4: '深圳'
      },
      orderList: {
        1: '未支付',
        2: '支付失败',
        3: '审核中',
        4: '审核失败',
        5: '代发货',
        6: '已发货',
        7: '交易成功',
        8: '已取消'
      }
    }
  }
}
</script>
<style scoped>
    .order-search{
        padding: 20px 0;
    }
</style>

