<template>

  <el-tabs v-model="activeName">
    <el-tab-pane label="快讯生成" name="first">
      <el-row>

        <ul>
          <li v-for="item in number" :key="item">
            <el-checkbox :label="item">
              <div class="title"></div>
              <el-input
              :rows="12"
              placeholder="hello"
              clearable>
              </el-input>
            </el-checkbox>
          </li>
        </ul>

      </el-row>
      <el-button-group>
        <el-button type="primary" icon="el-icon-refresh" size="medium"></el-button>
        <el-button type="primary" icon="el-icon-download" size="medium"></el-button>
      </el-button-group>
    </el-tab-pane>
    <el-tab-pane label="参数配置" name="second">参数配置</el-tab-pane>
  </el-tabs>
</template>

<script>

export default {
  name: 'HelloWorld',
  data () {
    return{
      activeName: 'first',
      number:[1,2,3,4,5]
    }
  },
  methods:{
    success(){
      axios({
        method: 'post',
        url: 'http://10.102.21.171:8000/news/read',
        data: {"start": 1,  "num": 3},
      })
    }, 
  }
  

}
</script>

<style scoped>
ul,li{
  list-style:none;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  margin-bottom: 30px;
}

</style>
