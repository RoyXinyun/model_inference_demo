<template>
  <div id="cut">
    <Title></Title>

    <el-row :gutter="20">
      <el-col :span="4">
        <div id="nav">
          <el-menu
            default-active="1"
            class="el-menu-vertical-demo"
            @select="handleSelect">

            <el-menu-item index="1" style="text-align: center">
              <span slot="title">模型切割</span>
            </el-menu-item>
            <el-menu-item index="2" style="text-align: center">
              <span slot="title">模型部署</span>
            </el-menu-item>
            <el-menu-item index="3" style="text-align: center">
              <span slot="title">模型测试</span>
            </el-menu-item>
          </el-menu>
        </div>
      </el-col>
      <el-col :span="20">
        <el-card class="box-card">
          <div slot="header">
            <span>通信限制条件</span>
            <el-button style="float: right; padding: 3px 0" type="text" @click="onClear">全部清空</el-button>
          </div>

          <div>
            <div class="input_model">
              <span>时延</span>
              <el-input v-model="delay" placeholder="请输入内容" class="input"></el-input>
            </div>
            <div class="input_model">
              <span>带宽</span>
              <el-input v-model="bandwidth" placeholder="请输入内容" class="input"></el-input>
            </div>

            <div style="text-align: right">
              <el-button type="primary">模型切割</el-button>
            </div>
          </div>

        </el-card>
      </el-col>
    </el-row>

    <div id="showres">
      <el-card class="card_res">
        <div slot="header">
          <span>模型切割结果</span>
          <el-button style="float: right; padding: 3px 0" type="text">刷新</el-button>
        </div>
        <div>
          <el-row>
            <el-col :span="12">
              <el-card class="yunduan" style="margin: 10px">
                <div slot="header" class="clearfix">
                  <span>云模型</span>
                </div>

                <div>
                  <el-table :data="tableData" style="width: 100%">
                    <el-table-column prop="date" label="模型精度">
                    </el-table-column>
                    <el-table-column prop="name" label="传输延迟">
                    </el-table-column>
                    <el-table-column prop="address" label="边端计算量">
                    </el-table-column>
                    <el-table-column prop="address" label="泛化情况">
                    </el-table-column>
                  </el-table>
                </div>

                <div style="float: right">
                  <div>
                    <el-button style="padding: 3px 0;color: #02A7F0" type="text">云模型架构文件下载</el-button>
                  </div>
                  <div>
                    <el-button style="padding: 3px 0;;color: #02A7F0" type="text">云模型参数文件下载</el-button>
                  </div>
                </div>
              </el-card>
            </el-col>
            <el-col :span="12">
              <el-card class="bianduan" style="margin: 10px">
                <div slot="header" class="clearfix">
                  <span>边模型</span>
                </div>

                <div>
                  <el-table :data="tableData" style="width: 100%">
                    <el-table-column prop="date" label="模型精度">
                    </el-table-column>
                    <el-table-column prop="name" label="传输延迟">
                    </el-table-column>
                    <el-table-column prop="address" label="边端计算量">
                    </el-table-column>
                    <el-table-column prop="address" label="泛化情况">
                    </el-table-column>
                  </el-table>
                </div>

                <div style="float: right">
                  <div>
                    <el-button style="padding: 3px 0;color: #02A7F0" type="text">边模型架构文件下载</el-button>
                  </div>
                  <div>
                    <el-button style="padding: 3px 0;;color: #02A7F0" type="text">边模型参数文件下载</el-button>
                  </div>
                </div>

              </el-card>
            </el-col>
          </el-row>
        </div>

      </el-card>
    </div>


  </div>

</template>

<script>
export default {
  name: "cutting",
  data() {
    return {
      delay: "",
      bandwidth: ""
    }

  },
  methods: {
    handleSelect(key, keyPath){
      if(key == '1'){
        this.$router.push('cutting')
      }else if(key == '2'){
        this.$router.push('arrange')
      }else if(key == '3'){
        this.$router.push('test')
      }
    },
    onClear() {
      this.delay = this.bandwidth = ""
    }
  }
}
</script>

<style scoped>
#cut {
  margin-left: 10%;
}

#showres {
  text-align: center;
  margin-top: 50px;
}


.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}

.clearfix:after {
  clear: both
}

.box-card {
  width: 600px;
  margin-left: 100px;
}

.input {
  width: 300px;
  margin-left: 7px;
}

.input_model {
  margin: 20px;
}

.card_res {
  width: 90%;
}

</style>
