<template>
  <div>
    <div class="nav">
      <h1>Demo_01</h1>
    </div>

    <div class="content">

      <!--v-model="dataValue" (input数据绑定)@keyup.enter="addData"(enter点击事件)-->
      <input type="text" class="content_data" placeholder="请输入数据" v-model="dataValue" @keyup.enter="addData"/>

      <!--v-show="!list.length"(表达式，布尔值，样式隐藏显示)-->
      <div class="content_data_show" v-show="!list.length">
        <span>
          <img src="../assets/01_提示成功.png"/>
          <a>&nbsp;暂无数据，请添加数据</a>
        </span>
      </div>

      <ul class="data_ul">
        <li class="data_li" v-for="item in list" :key="item.title">
          <label class="label">{{item.title}}</label>
          <span class="data_delete" @click="deleteApp(item)">
            <img src="../assets/04_提示错误.png"/>
          </span>
        </li>
      </ul>

      <span class="clean" @click="clean">清除</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'demo',
    data () {
        return {
            list: [],
            dataValue: ''
        }
    },
  methods: {
    addData: function () { // 添加数据
      this.list.push({ // 数组追加对象
        title: this.dataValue
      })
      this.dataValue = ''
    },
    deleteApp: function (dataValue) { // 删除数据
      let index = this.list.indexOf(dataValue) // 根据下标获取当前元素
      this.list.splice(index, 1) // 删除此下标对应的一个元素
    },
    clean: function () { // 清除数据
      this.list = []
    }
  }
}
</script>

<style scoped>
  .nav {
    width: 100%;
    background-color: #f2edf7;
    padding: 20px;
  }
  .content {
    width: 60%;
    background-color: azure;
    border: 1px solid #a6a6a6;
    margin: 50px auto;
    position: relative;
    text-align: center;
  }
  .content_data {
    width: 80%;
    margin-top: 40px;
    padding: 20px 30px;
  }
  .content_data_show {
    width: 80%;
    border: 1px solid #50dd69;
    margin: 40px auto 90px;
    padding: 20px 30px;
    text-align: left;
  }
  .content_data_show span {
    color: #50dd69;
  }
  /*.content_data_show span:before{*/
    /*content:url('../assets/01_提示成功.png');*/
    /*vertical-align:middle;*/
    /*display:inline-block;*/
    /*padding-right: 10px;*/
   /*}*/
  .clean {
    width: 80px;
    background-color: azure;
    cursor: pointer;
    position: absolute;
    bottom: 20px;
    right: 10%;
    line-height: 40px;
  }
  .clean:hover {
    background-color: rgba(129, 255, 210, 0.35);
  }
  .clean:active {
    background-color: #80ffb8;
  }
  .data_ul {
    padding: 0;
    margin-bottom: 90px;
  }
  .data_li {
    border-bottom: 1px solid #a6a6a6;
    list-style: none;
    width: 80%;
    margin: 20px auto;
    padding: 20px 30px;
    text-align: left;
  }
  .data_delete {
    position: absolute;
    right: 15%;
    cursor: pointer;
  }
</style>