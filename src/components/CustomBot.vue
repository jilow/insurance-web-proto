<template>
    <div class="chat-container">
      <div id="chat-icon" class="jump" v-on:click="toggleChatWindow()">
        <img src="../assets/bot-avatar.png"/>
      </div>
      <div id="chat" ref="chat">
        <div class="chat-background"></div>
      </div>
    </div>
</template>

<script>
import { Bubbles } from "../../node_modules/chat-bubble/component/Bubbles.js"
import { ApiAiClient } from "api-ai-javascript"
import anime from 'animejs'

export default {
  name: 'CustomBot',
  data() {
    return {}
  },
  methods: {
    initChatWindow(){
      if(!this.chatWindowInitialized){
        let chatWindow =  new Bubbles(document.getElementById("chat"), "chatWindow", {
          inputCallbackFn: function(o) {
            const client = new ApiAiClient({accessToken: '39181a37bd8340bb8e781c256e27e0fa'})
            const promise = client.textRequest(o.input)
            promise.then(function(serverResponse){
                //console.log(serverResponse)
                const response = serverResponse.result.fulfillment.speech
                chatWindow.talk({
                    "response": {
                        says: [response]
                    },
                },"response")
            }).catch(function(serverResponse){
              console.log(serverResponse)
            })
          }, 
          typeSpeed: 25,
        })
        this.chatWindow = chatWindow
        this.chatWindowInitialized = true
        this.initChat()
      }
      return this.chatWindow
    },
    initChat(){
      var convo = {
        ice: {
          says: ["Hello there, my name is Buzzz!", "I am here to help you insure a gadget.", "What is it that you're looking to insure?"],
        },
      }
      this.chatWindow.talk(convo)
    },
    hideChat(){
      anime({
        targets: this.$refs.chat,
        duration: 1500,
        opacity: 0
      });
      this.chatWindowOpen = false
    },
    showChat(){
      this.chatWindow = this.initChatWindow()
      this.chatWindowOpen = true
      anime({
        targets: this.$refs.chat,
        duration: 2500,
        opacity: 1
      });
    },
    toggleChatWindow(){
        if(this.chatWindowOpen){
            this.hideChat()
        }
        else{
            this.showChat()
        }    
    }
  },
  mounted(){
    this.chatWindowOpen = false
    this.chatWindowInitialized = false
  }
}
</script>

<style>

@import '../../node_modules/chat-bubble/component/styles/setup.css';
@import '../../node_modules/chat-bubble/component/styles/says.css';
@import '../../node_modules/chat-bubble/component/styles/reply.css';
@import '../../node_modules/chat-bubble/component/styles/typing.css';
@import '../../node_modules/chat-bubble/component/styles/input.css';

.bubble-container {
  width: 400px;
  position: fixed;
  bottom: 0;
  right: 4rem;
  font-size: 14px;
  background: #f5faff;
}
.bubble{
  background: #409eff;
  color: white;
}
.bubble-container .input-wrap textarea {
    width: calc(100% + 2px);
    margin: 1px 0px 0px -1px;
    resize: none;
    border-radius: 0;
    padding: 26px 15px 18px;
    vertical-align: middle;
    line-height: 8px;
    background: #353535;
    color: white;
}
.bubble-container .input-wrap textarea::placeholder{
  color: white;
}
.bubble.reply .bubble-content .bubble-button.bubble-pick{
  background: #353535;
}
.bubble-typing {
  width: 65px;
  height: 30px;
  background: #409eff;
}
#chat{
    width: 400px;
    height: 500px;
    position: fixed;
    bottom: 100px;
    right: 100px;
    display: block;
    opacity: 0;
    border-radius: 10px 10px 5px 10px;
    box-shadow: 0 2px 12px 0 rgba(0,0,0,.1);
    border: 1px solid #ebeef5;
}
#chat-icon{
    width: 60px;
    height: 60px;
    position: fixed;
    bottom: 45px;
    right: 45px;   
    cursor: pointer;         
}
#chat-icon img{
    position: relative;
    width: 60px;
    height: 60px;
}
.chat-background{
  height: 100%;
  width: 100%;
  background: url("../assets/gadget-doodle.jpg");
  opacity: 0.04;
}
.bubble.reply .bubble-content .bubble-button.bubble-pick{
    margin-bottom: 3px;
}
.input-wrap{
    height: 60px;
}
.bubble-wrap::-webkit-scrollbar {
	width: 10px;
}

.bubble-wrap::-webkit-scrollbar-thumb {
	border-radius: 5px;
	background: rgba(0,0,0,.1);
}
.jump {
    animation: jump 1s 2s forwards cubic-bezier(.84,-0.54,.31,1.19);
}
@keyframes jump {
    0% {
        transform: none;
    }
    50% {
        transform: translateY(-2em);
    }
}

</style>

