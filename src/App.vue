<template>

 <!-- 반복문 사용 -->
  <!-- <div v-for="(b,c) in products" :key="c">
    <h4>{{products[c]}}</h4>
    <p>{{prices[c]}}만원</p>
  </div> -->
 
  <div class="black-bg" v-if="모달창열림==true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>{{ 원룸들[선택된상품인덱스].content }}</p>
      <button @click="모달창열림=false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="작명 in 메뉴들" :key="작명">{{작명}}</a>
  </div>

  <!-- <div>
    <img :src=원룸들[0].image class="room-img">
    <h4 @click="모달창열림=true">{{products[0]}}</h4>
    <p>월세 : {{원룸들[0].price}}원</p>
    
    <button @click="신고수[0]++">허위매물신고</button> <span>신고수 : {{신고수[0]}}</span>
  </div> -->



  <div v-for="(a,i) in 원룸들" :key="i">
    <img :src=원룸들[i].image class="room-img">
    <h4 @click="상품클릭(i)">{{원룸들[i].title}}</h4>
    <p>월세 : {{원룸들[i].price}}원</p>
    <!-- @ -> v-on: -->
    <!-- <button @click="신고수[0]++">허위매물신고</button> <span>신고수 : {{신고수[0]}}</span> -->
  </div>

  <!-- <div>
    <img src="./assets/room1.jpg" class="room-img">
    <h4 @click="모달창열림=true">{{products[1]}}</h4>
    <p>50만원</p>
    <button @click="신고수[1]++">허위매물신고</button> <span>신고수 : {{신고수[1]}}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4>{{products[2]}}</h4>
    <p>40만원</p>
    <button @click="신고수[2]++">허위매물신고</button> <span>신고수 : {{신고수[2]}}</span>
  </div> -->

  <!-- 반복문 사용 -->
  <!-- <div v-for="(b,c) in products" :key="c">
    <h4>{{products[c]}}</h4>
    <p>{{prices[c]}}만원</p>
  </div> -->
 
</template>

<script>

import data from './post.js'

export default {
  name: 'App',
  data(){
    return{
      원룸들 : data,
      선택된상품인덱스 : null,
      모달창열림 : false,
      신고수 : [0,0,0], 
      메뉴들 : ['Home','Shop','About'],
      // products : ['역삼동원룸','천호동원룸','마포구원룸'],
    }
  },
  methods : {   
    상품클릭(인덱스) {
    this.선택된상품인덱스 = 인덱스;
    this.모달창열림 = true;
  }
  },
  components: {
  }
}
</script>

<style>
body{
  margin: 0;
  background: whitesmoke;
}
div {
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0,5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color : white;
  padding: 10px; 
}

.room-img{
  width: 500px;
  margin-top: 40px;
}
</style>
