<template>

  <div class="home">
    <img style="width:750px;height:auto;" alt="Vue logo" src="../assets/logo.png">
    
    <!-- <HelloWorld msg="대한민국 알바생이라면 "/> -->

    <!-- <iframe
    allow="microphone;"
    width="350"
    height="430"
    src="https://console.dialogflow.com/api-client/demo/embedded/11ff647c-17c3-41f2-9e8e-ed43758bc496">
</iframe>
       -->
       <section id="introduction" class="section introduction">
  <div class="container">
    <div class="col-md-4 banner-inner-wrapper">
      <div class="banner-text">
        <h1>Welcome to ALBALAW</h1>
        <p> </p>
        <p>대한민국 알바생이라면</p>
        <p>지금 바로 알바로와 함께하세요</p>
        <a href="http://pf.kakao.com/_xeJxbwxl" class="btn">카카오 플러스친구</a> </div>
      <!-- banner text --> 
    </div>
    <div class="row">
      <div class="col-md-4 col-sm-6">
        <div class="intro-content">
          <h1 style="margin-top: 50%;margin-left: 25%;">알바생</h1>
          <h1 style="margin-left: 25%;">부당대우</h1>
          <h1 style="margin-left: 25%;">이제 그만!</h1>
        </div>
      </div>
      <div class="col-md-5 col-sm-6">
        <div class="intro-content" >
          <p>근로기준법에 대해 궁금한 것이 있다면? </p>
          <P>고용주로 부터 부당대우를 받았는데 어떻게 할지 모르겠다면? </P>
          <p>지금 바로 간편하게 알바로에게 상담하세요! </p>
          <p>단순문의부터 임금체불 진정 서류 작성까지, </p>
          <P>간편하게 웹과 카카오톡에서 가능합니다.</p>
          <p>웹사이트 우측하단 버튼을 통해 사용해보세요!</p>
        </div>
      </div>
      
    </div>
  </div>
</section>
    <Chat class ="CDS"
        iconColorProp="#ffd500"
        messageOutColorProp="#4d9e93"
        messageInColorProp="#f1f0f0"
        messageBackgroundColorProp="#ffffff"
        :messageListProp="messageList"  
        :initOpenProp="initOpen"
        @onToggleOpen="handleToggleOpen"
        @onMessageWasSent="handleMessageReceived"
        

      />
      <!-- <strong>Output:</strong>
                        <div v-if="output.message != undefined" v-model="output">
                        {{output.message}}
                       
                        </div> -->
  
  <footer id="contact" class="footer">
  <div class="container">
    <div class="col-md-4">
      <h4>Contact</h4>
      <p> 
        Kakaotalk : albalaw 
        <br>Email : <a href="mailto:service@albalaw.co.kr "> service@albalaw.co.kr  </a></p>
    </div>
    
  
  </div>
</footer>
  </div>

 

</template>

<script>

// @ is an alias to /src
// mport HelloWorld from '@/components/HelloWorld.vue'

// export default {
//   name: 'home',
//   components: {
//     HelloWorld
//   }
// }i

import {Chat} from 'vue-chat-widget';
import axios from 'axios';
// main.js
import Vue from 'vue'


 
export default {
  
  name: "app",
  components: {
    Chat,
  },
  data: () => {
    return {
      messageList: [],
      initOpen: false,
      toggledOpen: false,
      name: '',
      description: '',
      output: ''

    }
  },
  // watch : {
  //   output: function() {
  //     this.handleMessageResponse(this.output.message);}
  //   },

  methods: {
  getDelayedData() {
    // Create a new Promise and resolve after 2 seconds
    var myTimerPromise = new Promise((resolve, reject) => {
        setTimeout(() => {
            // callback function for timer, gets called after the time-delay
            // Your timer is done now. Print a line for debugging and resolve myTimerPromise
            this.handleMessageResponse(this.output.message.text);
            console.log("2 seconds up, resolving myTimerPromise")
            resolve();
        }, 2000);  // This promise will be resolved in 2000 milli-seconds
    });

},
    // Send message from you
    handleMessageReceived(message) {
      
      console.log(message);
      this.messageList.push(message);
      
      let currentObj = this;
                axios.post('https://ipdfz5zbm5.execute-api.ap-northeast-2.amazonaws.com/new_beta/message', {
                    content: message.body,
                    user_key: 'webtester1',
                    type : 'text'
                })
                .then(function (response) {
                  
                    currentObj.output = response.data;
                    
                })
                .catch(function (error) {
                    currentObj.output = error;
                });
                console.log(this.output.length);

      
    this.getDelayedData();
    
    
    
        
    },
    // Receive message from them (handled by you with your backend)
    
    handleMessageResponse(message) {
       if (this.output.message != undefined) {
         this.messageList.push({ body: this.output.message.text, author: 'them' });
       }
       else{
         
         this.handleMessageResponse(this.output.message);
       }
            
            
    },
    // Chat toggled open event emitted
    handleToggleOpen(open) {
      this.toggledOpen = open
      // connect/disconnect websocket or something
    },
    

  },
  // init chat with a message
  mounted() {
    this.messageList.push({ body: '어떻게 도와드릴까요?', author: 'them' })
  },
  watch: {
    messageList: function(newList) {
      const nextMessage = newList[newList.length - 1]
      const isIncoming = (nextMessage || {}).author !== 'you'
      
    }
  }
}
</script>

<style>
img{
    opacity: 1;
    float: right;
    padding-right: 15%;
    top: -100px
}
.btn {
  text-decoration: none;
	border: 1px solid rgba(0, 0, 0, 0.75);
	margin-top: 20px;
	color: #2a2a2a;
	font-size: 12px;
	font-weight: 400;
	letter-spacing: 1px;
	border-radius: 0px;
	padding: 1.5% 3%;
	display: inline-block;
	text-transform: uppercase;
}
.footer {
	width: 94%;
	margin: auto;
	text-align: left;
	padding-top: 5%;
	padding-bottom: 7%;
  }
.footer h4 {
	font-size: 14px;
  text-align: left;
	color: #000;
	letter-spacing: 2px;
	margin: 195px 0 0 0;
	padding: 0px;
}
.intro-content {
	margin-top: 20px;
  text-align: left;
}
p {
	font-size: 18px;
	line-height: 22.4px;
	color: #6c7279;
}
h1 {
	font-size: 65px;
	color: #2d3033;
  
}
.row{
  margin-right:-15px;margin-left:-15px
  }
.container{
  padding-right:15px;padding-left:15px;margin-right:auto;margin-left:auto}
  @media (min-width:768px){
    .container{width:750px}}
    @media (min-width:992px){
      .container{width:970px}}
      @media (min-width:1200px){
        .container{width:1170px}}
        .container-fluid{padding-right:15px;padding-left:15px;margin-right:auto;margin-left:auto}
        .row{margin-right:-15px;margin-left:-15px}
        @media (min-width:768px){
          .col-sm-6,.col-sm-7,.col-sm-8,.col-sm-9{float:left}.col-sm-12{width:100%}
          .col-sm-11{width:91.66666667%}.col-sm-10{width:83.33333333%}.col-sm-9{width:75%}.col-sm-8{width:66.66666667%}.col-sm-7{width:58.33333333%}.col-sm-6{width:50%}
          }
          @media (min-width:992px){.col-md-4,.col-md-5,.col-md-6,.col-md-7,
          .col-md-8,.col-md-9{float:left}.col-md-12{width:100%}.col-md-11{width:91.66666667%}.col-md-10{width:83.33333333%}.col-md-9{width:75%}.col-md-8{width:66.66666667%}
          .col-md-7{width:58.33333333%}.col-md-6{width:50%}.col-md-5{width:41.66666667%; margin-top:15%; float: right}.col-md-4{width:33.33333333%; margin-top:5%; float: left;}.col-md-3{width:25%}.col-md-2{width:16.66666667%}
          .col-md-1{width:8.33333333%}.col-md-pull-12{right:100%}.col-md-pull-11{right:91.66666667%}.col-md-pull-10{right:83.33333333%}.col-md-pull-9{right:75%}
          .col-md-pull-8{right:66.66666667%}.col-md-pull-7{right:58.33333333%}.col-md-pull-6{right:50%}.col-md-pull-5{right:41.66666667%}.col-md-pull-4{right:33.33333333%}
          .col-md-pull-3{right:25%}.col-md-pull-2{right:16.66666667%}.col-md-pull-1{right:8.33333333%}.col-md-pull-0{right:auto}.col-md-push-12{left:100%}
          .col-md-push-11{left:91.66666667%}.col-md-push-10{left:83.33333333%}.col-md-push-9{left:75%}.col-md-push-8{left:66.66666667%}.col-md-push-7{left:58.33333333%}
          .col-md-push-6{left:50%}.col-md-push-5{left:41.66666667%}.col-md-push-4{left:33.33333333%}.col-md-push-3{left:25%}.col-md-push-2{left:16.66666667%}
          .col-md-push-1{left:8.33333333%}.col-md-push-0{left:auto}.col-md-offset-12{margin-left:100%}.col-md-offset-11{margin-left:91.66666667%}
          .col-md-offset-10{margin-left:83.33333333%}.col-md-offset-9{margin-left:75%}.col-md-offset-8{margin-left:66.66666667%}.col-md-offset-7{margin-left:58.33333333%}
          .col-md-offset-6{margin-left:50%}.col-md-offset-5{margin-left:41.66666667%}.col-md-offset-4{margin-left:33.33333333%}.col-md-offset-3{margin-left:25%}
          .col-md-offset-2{margin-left:16.66666667%}.col-md-offset-1{margin-left:8.33333333%}.col-md-offset-0{margin-left:0}}
</style>

