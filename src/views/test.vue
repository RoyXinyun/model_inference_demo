<template>
  <div id="test">
    <Title></Title>
    <el-row>
      <el-col :span="4">
        <div id="nav">
          <el-menu
            default-active="3"
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
        <div style="width: 700px;margin-left: 70px">
          <el-card class="image_card" style="margin: 10px">



          </el-card>
        </div>

      </el-col>

    </el-row>
  </div>


</template>

<script>
export default {
  name: "test",
  methods: {
    handleSelect(key, keyPath){
      if(key == '1'){
        this.$router.push('cutting')
      }else if(key == '2'){
        this.$router.push('arrange')
      }else if(key == '3'){
        this.$router.push('test')
      }
    }
  }
}
</script>

<style scoped>
#test {
  margin-left: 10%;
}

</style>
