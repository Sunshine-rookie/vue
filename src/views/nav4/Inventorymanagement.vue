<template>
<el-row>
    <el-col style="font-size:24px;margin:0;text-align:center;">库 存 管 理 </el-col>
    <el-col :span="24" class="container1" style="margin-top:10px;margin-top:10px;border: 1px solid rgba(204, 204, 204, 1);">
      <!-- 查询条件 -->
        <el-row class="title_">
          <el-col :span="24" style="margin:0;">查询条件
            <el-button size="mini" type="info" class="btn" >信息按钮</el-button>
          </el-col>
        </el-row>
        <el-col :span="24" style="width:100%;height:230px;padding-top:6px;">
          <el-row>
            <el-col :span="4">
              <el-form :label-position="labelPosition" label-width="80px" :model="formLabelAlign">
                <el-form-item label="">
                  <input type="radio" style="width:15px;height:15px;"><span>按单号查询</span>
                </el-form-item>
                <el-form-item label="">
                 <input type="radio" style="width:15px;height:15px;"><span>按客户单号查询&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;消息</span>
                </el-form-item>
                <el-form-item label="">
                  <el-input style="width:157x;" type="textarea" :rows="6" placeholder="请输入内容" v-model="textarea"></el-input>
                </el-form-item>
              </el-form>
            </el-col>
            <el-col :span="4">
              <el-form :label-position="labelPosition" label-width="100px" style="display:inline-block;margin:0;">
                <el-form-item label="仓位分类">
                  <el-select v-model="form.region1" placeholder="请选择">
                    <el-option label="全部库存" value="全部库存"></el-option>
                    <el-option label="干线待发仓" value="干线待发仓"></el-option>
                    <el-option label="中转仓" value="中转仓"></el-option>
                    <el-option label="派送仓" value="派送仓"></el-option>
                    <el-option label="自提仓" value="自提仓"></el-option>
                    <el-option label="异常仓" value="异常仓"></el-option>
                 </el-select>
                </el-form-item>
              </el-form>
              <el-form :label-position="labelPosition" label-width="80px" style="width: 255px;height: 115px;margin-top:18px;border: 1px solid rgba(204, 204, 204, 1);">
                  <div style="margin-top:6px;">
                    <input type="radio" value="入库时间" v-model="picked">
                    <label for="one">按入库时间查询</label>
                    <input type="radio" value="出库时间" v-model="picked">
                    <label for="two">按出库时间查询</label>
                  </div>
                  <div>
                    <el-form-item :label="picked">
                      <el-date-picker size="small" style="width:160px;" type="date" v-model="value1" placeholder="选择日期" :picker-options="pickerOptions0">
                      </el-date-picker>
                    </el-form-item>
                    <el-form-item label="至">
                      <el-date-picker size="small" style="width:160px;" type="date" v-model="value2" placeholder="选择日期" :picker-options="pickerOptions0">
                      </el-date-picker>
                    </el-form-item>
                  </div>
              </el-form>
            </el-col>
            <el-col :span="4">
              <el-form :label-position="labelPosition" label-width="100px" style="display:inline-block;margin:0;">
                <el-form-item label="始发站点">
                  <el-select v-model="form.region13" placeholder="请选择">
                   <el-option label="上海" value="上海"></el-option>
                   <el-option label="昆明" value="昆明"></el-option>
                   <el-option label="贵阳" value="贵阳"></el-option>
                   <el-option label="金华" value="金华"></el-option>
                   <el-option label="合肥" value="合肥"></el-option>
                   <el-option label="长沙" value="长沙"></el-option>
                   <el-option label="济南" value="济南"></el-option>
                   <el-option label="郑州" value="郑州"></el-option>
                   <el-option label="深圳" value="深圳"></el-option>
                   <el-option label="广州" value="广州"></el-option>
                   <el-option label="泉州" value="泉州"></el-option>
                   <el-option label="汕头" value="汕头"></el-option>
                 </el-select>
                </el-form-item>
                <el-form-item label="订单录入公司">
                  <el-input></el-input>
                </el-form-item>
                <el-form-item label="订单录入员">
                  <el-select v-model="form.region2" placeholder="请选择">
                    <el-option label="默认当前站点" value="默认当前站点"></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="订单录入员">
                  <el-select v-model="form.region3" placeholder="请选择">
                    <el-option label="当前站点" value="当前站点"></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="制单日期">
                  <el-date-picker size="small" style="width:160px;" type="date" v-model="value3" placeholder="选择日期" :picker-options="pickerOptions0">
                  </el-date-picker>
                </el-form-item>
              </el-form>
            </el-col>
            <el-col :span="4">
              <el-form :label-position="labelPosition" label-width="100px" style="display:inline-block;margin:0;">
                <el-form-item label="目的站点">
                  <el-select v-model="form.region4" placeholder="请选择">
                   <el-option label="上海" value="上海"></el-option>
                   <el-option label="昆明" value="昆明"></el-option>
                   <el-option label="贵阳" value="贵阳"></el-option>
                   <el-option label="金华" value="金华"></el-option>
                   <el-option label="合肥" value="合肥"></el-option>
                   <el-option label="长沙" value="长沙"></el-option>
                   <el-option label="济南" value="济南"></el-option>
                   <el-option label="郑州" value="郑州"></el-option>
                   <el-option label="深圳" value="深圳"></el-option>
                   <el-option label="广州" value="广州"></el-option>
                   <el-option label="泉州" value="泉州"></el-option>
                   <el-option label="汕头" value="汕头"></el-option>
                 </el-select>
                </el-form-item>
                <el-form-item label="目的省份">
                  <el-select v-model="form.region5" placeholder="请选择">
                   <el-option label="上海" value="上海"></el-option>
                   <el-option label="昆明" value="昆明"></el-option>
                   <el-option label="贵阳" value="贵阳"></el-option>
                   <el-option label="金华" value="金华"></el-option>
                   <el-option label="合肥" value="合肥"></el-option>
                   <el-option label="长沙" value="长沙"></el-option>
                   <el-option label="济南" value="济南"></el-option>
                   <el-option label="郑州" value="郑州"></el-option>
                   <el-option label="深圳" value="深圳"></el-option>
                   <el-option label="广州" value="广州"></el-option>
                   <el-option label="泉州" value="泉州"></el-option>
                   <el-option label="汕头" value="汕头"></el-option>
                 </el-select>
                </el-form-item>
                <el-form-item label="目的城市">
                  <el-select v-model="form.region6" placeholder="请选择">
                   <el-option label="上海" value="上海"></el-option>
                   <el-option label="昆明" value="昆明"></el-option>
                   <el-option label="贵阳" value="贵阳"></el-option>
                   <el-option label="金华" value="金华"></el-option>
                   <el-option label="合肥" value="合肥"></el-option>
                   <el-option label="长沙" value="长沙"></el-option>
                   <el-option label="济南" value="济南"></el-option>
                   <el-option label="郑州" value="郑州"></el-option>
                   <el-option label="深圳" value="深圳"></el-option>
                   <el-option label="广州" value="广州"></el-option>
                   <el-option label="泉州" value="泉州"></el-option>
                   <el-option label="汕头" value="汕头"></el-option>
                 </el-select>
                </el-form-item>
                <el-form-item label="派送方式">
                    <el-select v-model="form.region7" placeholder="请选择">
                      <el-option label="派送" value="派送"></el-option>
                      <el-option label="自提" value="自提"></el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="收货客户">
                  <el-input></el-input>
                </el-form-item>
              </el-form>
            </el-col>
            <el-col :span="4">
              <el-form :label-position="labelPosition" label-width="100px" style="display:inline-block;margin:0;">
                <el-form-item label="是否预约">
                  <el-select v-model="form.region8" placeholder="请选择">
                      <el-option label="有预约" value="有预约"></el-option>
                      <el-option label="未预约" value="未预约"></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="是否有回单">
                  <el-select v-model="form.region9" placeholder="请选择">
                      <el-option label="有回单" value="有回单"></el-option>
                      <el-option label="有回单" value="有回单"></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="件数">
                  <el-input></el-input>
                </el-form-item>
                <el-form-item label="品名">
                  <el-input></el-input>
                </el-form-item>
                <el-form-item label="手机号码">
                  <el-input></el-input>
                </el-form-item>
              </el-form>
            </el-col>
            <el-col :span="4">
              <el-form :label-position="labelPosition" label-width="100px" style="display:inline-block;margin:0;">
                <el-form-item label="付款方式">
                  <el-select v-model="form.region10" placeholder="请选择">
                      <el-option label="现付" value="现付"></el-option>
                      <el-option label="到付" value="到付"></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="业务员">
                  <el-select v-model="form.region11" placeholder="请选择">
                      <el-option label="123" value="123"></el-option>
                      <el-option label="456" value="456"></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="是否有到付款">
                  <el-select v-model="form.region12" placeholder="请选择">
                      <el-option label="是" value="是"></el-option>
                      <el-option label="否" value="否"></el-option>
                  </el-select>
                </el-form-item>
              </el-form>
            </el-col>
            <div style="margin-top:18px;display:inline-block;">
              <el-button style="width:100px;height:30px;" type="info" size="small">添加查询条件</el-button>
              <el-button style="width:100px;height:30px;margin-right:30px;border:0;background:#999999;" type="info" size="small">预约登记</el-button>
              <el-button style="width:100px;height:30px;margin-right:30px;border:0;background:#999999;" type="info" size="small">转换仓位</el-button>
              <el-button style="width:120px;height:30px;margin-right:30px;border:0;background:#999999;" type="info" size="small">编辑摆放摆放标记</el-button>
            </div>
          </el-row>
        </el-col>

    </el-col>
    <!-- 查询结果 -->
    <el-col :span="24" style="margin-top:6px;border: 1px solid rgba(204, 204, 204, 1);">
      <el-col :span="24" class="title_">查询结果
        <el-button size="mini" type="info" class="btn" >导出Excel</el-button>
        <el-button size="mini" type="info" class="btn" >显示设置</el-button>
      </el-col>
      <el-col :span="24" style="height:100%;margin:10px;">
        <el-table :data="tableData6" border show-summary style="width: 99%" max-height="250">
            <el-table-column type="index" label="序号" width="80"></el-table-column>
            <el-table-column prop="name" label="姓名"> </el-table-column>
            <el-table-column prop="amount1" sortable label="数值 1" width="120"></el-table-column>
            <el-table-column prop="amount2" label="数值 2"></el-table-column>
            <el-table-column prop="amount3" label="数值 3"></el-table-column>
            <el-table-column prop="name" width="150" label="选择"></el-table-column>
            <el-table-column prop="name" width="150" label="入库日期"></el-table-column>
            <el-table-column prop="name" width="150" label="始发站点"></el-table-column>
            <el-table-column prop="name" width="150" label="目的站点"></el-table-column>
            <el-table-column prop="name" width="150" label="运单编号"></el-table-column>
            <el-table-column prop="name" width="150" label="增值服务"></el-table-column>
            <el-table-column prop="name" width="150" label="发货客户"></el-table-column>
            <el-table-column prop="name" width="150" label="发货联系人"></el-table-column>
            <el-table-column prop="name" width="150" label="收货客户"></el-table-column>
            <el-table-column prop="name" width="150" label="收货联系人"></el-table-column>
            <el-table-column prop="name" width="150" label="手机号码"></el-table-column>
            <el-table-column prop="name" width="150" label="座机号码"></el-table-column>
            <el-table-column prop="name" width="150" label="目的省份"></el-table-column>
            <el-table-column prop="name" width="150" label="目地城市"></el-table-column>
            <el-table-column prop="name" width="150" label="目地区/县"></el-table-column>
        </el-table>
      </el-col>
    </el-col>
</el-row>
</template>
<script>
  export default {
    data() {
      return {
        labelPosition: 'right',
        formLabelAlign: {
          amount1: '',
          region: '',
          type: ''
        },
        form: {
          name: '',
          region1: '',
          region2: '',
          region3: '',
          region4: '',
          region5: '',
          region6: '',
          region7: '',
          region8: '',
          region9: '',
          region10: '',
          region11: '',
          region12: '',
          region13: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
        pickerOptions0: {
          disabledDate(time) {
            return time.getTime() < Date.now() - 8.64e7;
          }
        },
        value1:'',
        value2:'',
        value3:'',
        picked: '入库时间',
        textarea:'',
        radio2:3,
        isShow:true,
        tableData: [
          {
            date: '',
            amount1: '',
            address: ''
          }
        ],
        tableData6: [
          {
            name: '王小虎',
            amount1: '234',
            amount2: '3.2',
            amount3: 10
          }, {
            name: '王小虎',
            amount1: '165',
            amount2: '4.43',
            amount3: 12
          }, {
            name: '王小虎',
            amount1: '324',
            amount2: '1.9',
            amount3: 9
          }, {
            name: '王小虎',
            amount1: '621',
            amount2: '2.2',
            amount3: 17
          }, {
            name: '王小虎',
            amount1: '539',
            amount2: '4.1',
            amount3: 15
          }
        ]
      }
    },
    methods:{
      delete1() {
        this.$confirm('您确定要删除此信息, 是否继续?', '提示', {
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
      change1(){
        alert(1)
      }
    }
  }
</script>
<style scoped>
    #head{
      width: 100%;
      height: 65px;
      border: 1px solid rgba(204, 204, 204, 1);
      position: relative;
    }
    #head img{
      position: absolute;
      left: 103px;
      top: 1px;
      width: 227px;
      height: 64px;
    }

   .title_ {
       height: 34px;
       background: #eef1f6;
       line-height: 34px;
       border-left: 5px solid #e57715;
       font-size: 13px;
       font-weight: 800;
       padding-left:3px;
    }
  .el-form{
    height: 35px;
    display:inline-block;
  }
  .el-form-item {
    margin-bottom: 0;
  }
  .el-radio-group .el-radio {
      margin-top: 10px;
      margin-left: 2px;
  }
  .el-radio+.el-radio {
      margin-left: 8px;
  }
  .btn {
      background:#fff;
      color:#50bfff;
      float:right;
      margin-right:15px;
      margin-top: 6px;
  }
</style>