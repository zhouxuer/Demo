<template>
  <div>
    <div class="nav">
      <h1>Demo_01</h1>
    </div>

    <div class="content">

      <!--v-model="dataValue" (input数据绑定)
      @keyup.enter="addData"(enter点击事件)-->
      <input
        type="text"
        class="content-data"
        placeholder="请输入数据"
        v-model="dataValue"
        @keyup.enter="addData"
      />

      <!--v-show="!listArr.length"(表达式，布尔值，样式隐藏显示)-->
      <div class="content-data-show" v-show="!listArr.length">
        <img src="../assets/success.png"/>
        <span>&nbsp;暂无数据，请添加数据</span>
      </div>

      <ul class="data-list-show">
        <li class="data-line" v-for="(item,index) in listArr" :key="index">
          {{item.title}}
          <span class="data-delete" @click="deleteData(item)">
            <img src="../assets/error.png"/>
          </span>
        </li>
      </ul>

      <span class="delete-all" @click="deleteAll">清除</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'demo',
  data () {
    return {
      listArr: [],
      dataValue: ''
    }
  },
  methods: {
    addData: function () { // 添加数据
      if (this.dataValue !== '') {
        this.listArr.push({ // 数组追加对象
          title: this.dataValue
        })
        this.dataValue = ''
      }
    },
    deleteData: function (dataValue) { // 删除数据
      let index = this.listArr.indexOf(dataValue) // 根据下标获取当前元素
      this.listArr.splice(index, 1) // 删除此下标对应的一个元素
    },
    deleteAll: function () { // 清除数据
      this.listArr = []
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
  .content-data {
    width: 80%;
    margin-top: 40px;
    padding: 20px 30px;
  }
  .content-data-show {
    width: 80%;
    border: 1px solid #50dd69;
    margin: 40px auto 90px;
    padding: 20px 30px;
    text-align: left;
  }
  .content-data-show img {
    display: inline-block;
  }
  .content-data-show span {
    color: #50dd69;
  }
  .delete-all {
    width: 80px;
    background-color: azure;
    cursor: pointer;
    position: absolute;
    bottom: 20px;
    right: 10%;
    line-height: 40px;
  }
  .delete-all:hover {
    background-color: rgba(129, 255, 210, 0.35);
  }
  .delete-all:active {
    background-color: #80ffb8;
  }
  .data-list-show {
    padding: 0;
    margin-bottom: 90px;
  }
  .data-line {
    border-bottom: 1px solid #a6a6a6;
    list-style: none;
    width: 80%;
    margin: 20px auto;
    padding: 20px 30px;
    text-align: left;
  }
  .data-delete {
    position: absolute;
    right: 20%;
    cursor: pointer;
  }
  @media (min-width: 1024px) {
    .content {
      width: 40%;
    }
    .content-data {
      width: 60%;
      padding: 20px 15px;
    }
    .content-data-show {
      width: 60%;
      padding: 20px 15px;
    }
    .data-line {
      width: 60%;
      padding: 20px 15px;
    }
  }
  @media (max-width: 1024px) {
    .data-delete {
      position: absolute;
      right: 10%;
      cursor: pointer;
    }
  }
   @media (max-width: 768px) {
    .content {
      width: 80%;
    }
    .content-data {
      width: 60%;
      padding: 20px 15px;
    }
    .content-data-show {
      width: 60%;
      padding: 20px 15px;
    }
    .data-line {
      width: 60%;
      padding: 20px 15px;
    }
    .data-delete {
      position: absolute;
      right: 20%;
      cursor: pointer;
    }
  }
   @media (max-width: 414px) {
    .content {
      width: 100%;
    }
  }
</style>
