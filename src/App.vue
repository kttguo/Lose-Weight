<template>
  <div  id='header' >
   
    <h1 class="h1">每个人每天需要摄入的能量是多少</h1> 

    <div class="mb-3 mt-3 form-floating  container">
      <input type="number" v-model.number="weight" class="form-control" id="weight" placeholder="请输入您的体重"/>
      <label class="form-label" for="weight">请输入您的身高(cm)</label>
      
      <div class="form-floating mb-3 mt-3">
        <select v-model.number="option" class="form-select" placeholder="标准体重每千克的耗能" id="option">
          <option value="25">基本不运动：25</option>
          <option value="30">大部分时间都是坐着的：30</option>
          <option value="35">大部分时间都在运动：35</option>
          <option value="40">重体力劳动：40</option>
        </select>
        <label class="form-label" for="option">请选择您的活动量</label>
      </div>
      <div class="p-5 bg-success text-white text-center " v-show="weight!=0 &&option!=0" >
       <h2>您每天摄入的热量为：{{ (weight - 105) * option }}卡路里</h2>  
      </div>

    </div>
  </div>


  <div class=" row" v-show="weight!=0 &&option!=0">
    <div class=" card col-sm-6 col-md-4 col-lg-4">
      <h4 class="card-header bg-success text-white"> 您每天应该摄入碳水 {{ ((((weight - 105) * option)*0.55)/4).toFixed(1) }}克</h4>
      <img src="../public/image/谷物.png" alt="优质碳水谷物" class="img-fluid">
      <img src="../public/image/主食1.png" alt="优质碳水" class="img-fluid">  
      <div class="card-body ">
        <!-- <h4 class="card-title bg-success text-white">卡片标题</h4> -->
        <p class="card-text">在实际生活中，可以将这些碳水化合物一分为二，一半是粗粮和谷署，一半是米面</p>
      </div>
    </div>
    <div class="card col-sm-6 col-md-4 col-lg-4">
      <h4 class="card-header bg-success text-white">您每天应该摄入蛋白质{{ ((((weight - 105) * option)*0.15)/4).toFixed(1) }}克</h4>
      <img src="../public/image/蛋白质.png" alt="优质蛋白质" class="img-fluid"> 
      <div class="card-body ">
        <!-- <h4 class="card-title bg-success text-white">卡片标题</h4> -->
        <p class="card-text">一个中等大小的鸡蛋差不多含有6克蛋白质，200毫升牛奶含有6克蛋白质，瘦肉基本上含有17%-20%的蛋白质，既每100克肉含有17-20克蛋白质</p>
      </div>
    </div>
    <div class="card col-sm-6 col-md-4 col-lg-4">
      <h4 class="card-header bg-success text-white">您每天应该摄入脂质{{ ((((weight - 105) * option)*0.30)/9).toFixed(1) }}克</h4>
      <img src="../public/image/油脂.jpeg" alt="油脂" class="img-fluid">
      <div class="card-body ">
        <!-- <h4 class="card-title bg-success text-white">卡片标题</h4> -->
        <p class="card-text">植物油占有一半，每天为{{ (((((weight - 105) * option)*0.30)/9)/2).toFixed(1) }}克.动物油在吃鸡蛋和肉类食物喝牛奶的过程中可以获得</p>
      </div>

    </div>

  </div>
</template>

<script>

import { ref } from "vue";
export default {
  name: "App",
  setup() {
    const weight = ref("");
    const option = ref("");
    let calorie = (weight.value - 105) * option.value;

    return { weight, option, calorie };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: rgb(185,223,139)  ;
}


</style>
