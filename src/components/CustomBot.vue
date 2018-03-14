<template>
    <div class="chat-container">
      <div id="chat-icon" class="jump" v-on:click="toggleChatWindow()">
        <img src="img/robot_icon.png"/>
      </div>
      <div id="chat"></div>
    </div>
</template>

<script>
import { Bubbles } from "../../node_modules/chat-bubble/component/Bubbles.js"
import { ApiAiClient } from "api-ai-javascript";

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
      document.getElementById("chat").style.opacity = 0
      this.chatWindowOpen = false
    },
    showChat(){
      console.log("showing chat")
      this.chatWindow = this.initChatWindow()
      document.getElementById("chat").style.opacity = 1
      this.chatWindowOpen = true
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
    this.chatWindowOpen = false;
    this.chatWindowInitialized = false;
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
}
.bubble-container .input-wrap textarea {
    width: calc(100%);
    margin: 0;
    resize: none;
    border-radius: 0;
    padding: 26px 15px 18px;
    vertical-align: middle;
    line-height: 8px;
}
.bubble-typing {
	width: 65px;
}
#chat{
    width: 400px;
    height: 500px;
    position: fixed;
    bottom: 100px;
    right: 100px;
    display: block;
    opacity: 0;
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
.bubble.reply .bubble-content .bubble-button.bubble-pick{
    margin-bottom: 3px;
}
.input-wrap{
    height: 60px;
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

