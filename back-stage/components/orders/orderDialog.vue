<template>
  <div id='OrderDialog'>
    <div v-if="editType === 'service'">
      <label>客服操作</label>
      <el-input v-for="(item, index) in obj" :key="index" :value="item" :class="index"></el-input>
    </div>
    <div v-if="editType === 'shop'">
      <label>商家操作</label>
      <el-input placeholder="请输入内容"></el-input>
    </div>
    <span slot="footer" class="dialog-footer">
      <el-button @click="close1">取 消</el-button>
      <el-button type="primary" @click="close">确 定</el-button>
    </span>
  </div>
</template>
<script>
import { mapGetters, mapState } from 'vuex'
export default {
  computed: mapState({
    editType: ({order}) => order.editType.type,
    obj: ({order}) => order.editType.obj
  }),
  methods: {
    close () {
      let changeObj = {}
      for (let k in this.obj) {
        if (document.getElementsByClassName(k)[0].children[0].value !== '') {
          changeObj[k] = document.getElementsByClassName(k)[0].children[0].value
        } else {
          changeObj[k] = this.obj[k]
        }
      }
      this.$store.dispatch('orderEditType', {
        type: this.editType,
        obj: changeObj
      })
      this.$emit('close', false, this.obj)
    },
    close1 () {
      this.$emit('close', false)
    }
  }
}
</script>
<style scoped>

</style>
