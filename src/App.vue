<template>
 

  <div class="black-bg" v-if="openModel == true">
    <div class="white-bg" >
        <h2>상세페이지</h2>
        <p>상세페이지 내용</p>
        <button class="bt-size" @click="openModel = false">닫기</button>
    </div>
  </div>


  <div class="menu">
    <a v-for="(MS,i) in menus" :key="i">{{MS}}</a>
  </div>

 <div v-for="(main,i) in products" :key="i">
   <img :src="imgs[i].room" class="room-img">
    <h4 @click="openModel = true ">{{products[i]}} </h4>
    <p>{{prices[i]}} 만원</p>
    <button @click="DCRNUM[i] ++">허위매물신고</button> <span>들어온 신고: {{DCRNUM[i]}} </span>
 </div>
  <p v-for="(change,j) in changes" :key="j">
    <button class="bt_set" :style="{background : choice}" @click="changecolor">{{j+1}}</button>
  </p>



</template>

<script>


export default {
  name: 'App',
  data(){ //state라고 불림
    return{
      choice :'red',
        openModel : false,
        imgs :[{
           room : require("@/assets/room1.jpg")
        },
        {
          room : require("@/assets/room2.jpg")
        },
        {
          room : require("@/assets/room0.jpg")
        }   
        ],
      changes:[0],
        DCRNUM : [0,0,0],
        prices : [70,80,90],
        menus : ['Home','Shop','About'],
       products : ['역삼동원룸','천호동원룸','마포구원금'],
       
    }
  },

  methods : {
    changecolor(){
      if (this.bt.toString()=="1"){
      console.log("change")
      this.choice = 'blue'
      }
      },
    increase(){
      this.신고수+= 1;
    }
  },

  components: {
  
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  
}
.bt_set{
  font-size: 15px;
  color:white;
  font-family: "Segoe UI Symbol";
  border: none;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color : white;
  padding: 10px;
}

.room-img{
  width: 300px;
  margin-top: 40px;
}
body {
  margin : 0
}
div {
  box-sizing:border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background:rgba(0,0,0,0.5);
  position:fixed;padding:20px;
}
.white-bg{
  width: 100%; background: white;
  height: 20%;
  border-radius: 8px;
  padding:20px;
}
.bt-size {
  width: 100px;
  float: right;
  margin-right: 30px;
  background: #2c3e50;
  color: aliceblue;
  margin-top: 30px;
  font-family:-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 15px;
  
}
</style>
