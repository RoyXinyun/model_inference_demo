<template>
  <div id="arrange">
    <Title></Title>

    <el-row>
      <el-col :span="4">
        <div id="nav">
          <el-menu
            default-active="2"
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
        <div style="width: 80%;margin-left: 70px">
          <el-row :gutter="20">
            <el-col :span="12">
              <el-card class="yunduan" style="margin: 10px">
                <div slot="header" class="clearfix">
                  <span>云模型部署</span>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span class="font_style">IP地址</span>
                    </el-col>

                    <el-col :span="18">
                      <el-input v-model="cloud_ip" placeholder="请输入内容" class="input"></el-input>
                    </el-col>
                  </el-row>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span class="font_style">端口号</span>
                    </el-col>

                    <el-col :span="18">
                      <el-input v-model="cloud_post" placeholder="请输入内容" class="input"></el-input>
                    </el-col>
                  </el-row>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span style="text-align: left" class="font_style">模型架构文件</span>
                    </el-col>
                    <el-col :span="18" style="text-align: left">
                      <el-upload class="upload-demo"
                                 action="https://jsonplaceholder.typicode.com/posts/"
                                 :on-preview="handlePreview" :on-remove="handleRemove" :before-remove="beforeRemove"
                                 multiple :limit="1" :on-exceed="handleExceed" :file-list="fileList">

                        <el-button size="small" type="primary">点击上传</el-button>
                        <span slot="tip" class="el-upload__tip" style="margin-left: 5px">不超过500kb</span>
                      </el-upload>

                    </el-col>
                  </el-row>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span style="text-align: left" class="font_style">模型参数文件</span>
                    </el-col>
                    <el-col :span="18" style="text-align: left">

                      <el-upload class="upload-demo"
                                 action="https://jsonplaceholder.typicode.com/posts/"
                                 :on-preview="handlePreview" :on-remove="handleRemove" :before-remove="beforeRemove"
                                 multiple :limit="1" :on-exceed="handleExceed" :file-list="fileList">
                        <el-button size="small" type="primary">点击上传</el-button>
                        <span slot="tip" class="el-upload__tip" style="margin-left: 5px">不超过500kb</span>
                      </el-upload>
                    </el-col>
                  </el-row>
                </div>

                <div style="text-align: right">
                  <el-button type="primary" size="small">云模型部署</el-button>
                </div>

              </el-card>
            </el-col>
            <el-col :span="12">
              <el-card class="bianduan" style="margin: 10px">
                <div slot="header" class="clearfix">
                  <span>边模型部署</span>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span class="font_style">IP地址</span>
                    </el-col>

                    <el-col :span="18">
                      <el-input v-model="edge_ip" placeholder="请输入内容" class="input"></el-input>
                    </el-col>
                  </el-row>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span class="font_style">端口号</span>
                    </el-col>

                    <el-col :span="18">
                      <el-input v-model="edge_post" placeholder="请输入内容" class="input"></el-input>
                    </el-col>
                  </el-row>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span style="text-align: left" class="font_style">模型架构文件</span>
                    </el-col>
                    <el-col :span="18" style="text-align: left">
                      <el-upload class="upload-demo"
                                 action="https://jsonplaceholder.typicode.com/posts/"
                                 :on-preview="handlePreview" :on-remove="handleRemove" :before-remove="beforeRemove"
                                 multiple :limit="1" :on-exceed="handleExceed" :file-list="fileList">

                        <el-button size="small" type="primary">点击上传</el-button>
                        <span slot="tip" class="el-upload__tip" style="margin-left: 5px">不超过500kb</span>
                      </el-upload>

                    </el-col>
                  </el-row>
                </div>

                <div class="input_model">
                  <el-row :gutter="20">
                    <el-col :span="6">
                      <span style="text-align: left" class="font_style">模型参数文件</span>
                    </el-col>
                    <el-col :span="18" style="text-align: left">

                      <el-upload class="upload-demo"
                                 action="https://jsonplaceholder.typicode.com/posts/"
                                 :on-preview="handlePreview" :on-remove="handleRemove" :before-remove="beforeRemove"
                                 multiple :limit="1" :on-exceed="handleExceed" :file-list="fileList">
                        <el-button size="small" type="primary">点击上传</el-button>
                        <span slot="tip" class="el-upload__tip" style="margin-left: 5px">不超过500kb</span>
                      </el-upload>
                    </el-col>
                  </el-row>
                </div>

                  <div style="text-align: right">
                    <el-button type="primary" size="small">边模型部署</el-button>
                  </div>
              </el-card>
            </el-col>
          </el-row>
        </div>

      </el-col>
    </el-row>

  </div>

</template>

<script>
export default {
  name: "arrange",
  data() {
    return {
      fileList: [{
        name: 'food.jpeg',
        url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'
      }]
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      if (key == '1') {
        this.$router.push('cutting')
      } else if (key == '2') {
        this.$router.push('arrange')
      } else if (key == '3') {
        this.$router.push('test')
      }
    },
    handleRemove(file, fileList) {
      console.log(file, fileList);
    },
    handlePreview(file) {
      console.log(file);
    },
    handleExceed(files, fileList) {
      this.$message.warning(`当前限制选择 1 个文件，本次选择了 ${files.length} 个文件，共选择了 ${files.length + fileList.length} 个文件`);
    },
    beforeRemove(file, fileList) {
      return this.$confirm(`确定移除 ${file.name}？`);
    }
  }
}
</script>

<style scoped>
#arrange {
  margin-left: 10%;
}

.input {
  height: 15px;
}

.input_model {
  margin: 20px;
  width: 80%;
}
.input_model2 {
  margin: 20px;
}

.font_style {
  font-size: small;
}

</style>
