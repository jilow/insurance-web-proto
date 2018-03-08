<template>
  <iframe 
    class="chatbox"
    width="350"
    height="430"
    src="https://console.dialogflow.com/api-client/demo/embedded/7ed6abff-561c-4c4b-9a16-1ed1955c92eb">
  </iframe>
</template>

<script>
export default {
  name: 'DialogflowBox',
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

</style>

