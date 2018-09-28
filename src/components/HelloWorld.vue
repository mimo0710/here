<template>
  <el-tabs v-model="activeName">
    <el-tab-pane label="快讯生成" name="first">
      <el-row>
        <ul>
          <li v-for="item in need" :key="item">
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
    <el-tab-pane label="参数配置" name="second">
        <el-input
          type="textarea"
          :rows="10"
          placeholder="请输入内容"
          v-model="textarea">
        </el-input>
      <el-button-group style="margin-top:30px">
        <el-button type="primary" icon="el-icon-view" size="medium"></el-button>
        <el-button type="primary" icon="el-icon-download" size="medium"></el-button>
      </el-button-group>
    </el-tab-pane>
  </el-tabs>
</template>

<script>

export default {
  name: 'HelloWorld',
  data () {
    return {
      activeName: 'first',
      need:[],
      textarea: ''
    }
  },
  async created() {
    await this.success()
  },
  methods:{
    success(){
      this.$axios.post('http://10.102.21.171:8000/news/read',{"start": 0,  "num": 5})
    .then(function (response) {
      // this.need=response.data.message;
      console.log(response);
      console.log(this.need);
    })
    .catch(function (error) {
      console.log(error)
    })
    }
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
