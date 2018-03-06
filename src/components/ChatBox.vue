<template>
  <div class="chatbox">
    <div class="container">
      <div class="chatlog">
        <div class="message bot">
          <div class="avatar"></div>
          <p class="content">Hi, how can I help you?</p>
        </div>
        <div class="message self">
          <div class="avatar"></div>
          <p class="content">Hello, I need insurance on this</p>
        </div>
        <div class="message self">
          <div class="avatar"></div>
          <p class="content">iphone</p>
        </div>
      </div>
      <div class="input-area">
        <el-input placeholder="Write something..."></el-input>
        <el-button type="primary">Send</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ChatBox',
  data() {
    return {
    }
  },
}
</script>

<style scoped>

.chatbox {
  position: fixed;
  bottom: 0;
  right: 4rem;
  font-size: 14px;
}

.container {
  width: 100%;
  max-width: 16rem;
	min-width: 14rem;
  height: 100%;
  max-height: 60vh;
  min-height: 20rem;
	background: #fff;
  margin-bottom: 0.4rem;
  border: 1px solid #e8e8e8;
  box-shadow: 0 2px 12px 0 rgba(0,0,0,.1);
  border-radius: 0.5rem;
  padding: 1rem;
}

.chatlogs {
  display: flex;
  align-self: flex-start;
  width: 100%;
  height: 100%;
	overflow-x: hidden;
	overflow-y: scroll;
}

.chatlogs::-webkit-scrollbar {
	width: 10px;
}

.chatlogs::-webkit-scrollbar-thumb {
	border-radius: 5px;
	background: rgba(0,0,0,.1);
}

.message {
  display: flex;
	flex-flow: row wrap;
  align-items: flex-start;
  flex-direction: row;
	margin-bottom: 10px;
}

.message > .content {
  max-width: 80%;
  padding: 0.6rem 0.8rem;
  margin-top: 0;
  margin-left: 0.5rem;
  margin-bottom: 1rem;
	border-radius: 10px;
	color: #fff;
  background: #1adda4;
}

.message > .avatar {
  width: 2rem;
  height: 2rem;
  background: #e8e8e8;
  background-image: url('../assets/bot-avatar.png');
  background-position: center;
  background-size: cover;
	border-radius: 50%;
}

.message.self {
  
}

.message.self > .avatar {
  background-image: url('../assets/user-avatar.png');
}

.message.self > .content {
  background: #1ddced;
  order: -1;
  margin-left: auto;
  margin-right: 0.5rem;
}

.input-area {
  display: flex;
  align-self: flex-end;
}

</style>
