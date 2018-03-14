<template>
    <div id="chat"></div>
</template>

<script>
import { Bubbles } from "../../node_modules/chat-bubble/component/Bubbles.js"
import {ApiAiClient} from "api-ai-javascript";

export default {
  name: 'CustomBot',
  data() {
    return {}
  },
  methods: {
    initApiAiClient(){
      return new ApiAiClient({accessToken: '39181a37bd8340bb8e781c256e27e0fa'});
    },
    initChatWindow(client){
      let chatWindow =  new Bubbles(document.getElementById("chat"), "chatWindow", {
        inputCallbackFn: function(o) {
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
        }
      })
      return chatWindow
    },
    initChat(chatWindow){
      var convo = {
        ice: {
          says: ["Hello there!", "I am able to help you insure a gadget.", "Which gadget would you like to insure?"],
        },
      }
      chatWindow.talk(convo)
    }
  },
  mounted(){
    const client = this.initApiAiClient()
    this.chatWindow = this.initChatWindow(client)
    this.initChat(this.chatWindow)
  }
}
</script>

<style scoped>

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
    margin: 0;
    resize: none;
}

</style>

