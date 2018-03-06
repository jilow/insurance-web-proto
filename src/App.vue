<template>
  <div id="app">
    <site-header/>
    <router-view/>
    <chat-box/>
  </div>
</template>

<script>
import SiteHeader from '@/components/SiteHeader'
import ChatBox from '@/components/ChatBox'

export default {
  name: 'app',
  head: {
    link: [
      { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css?family=Quicksand:400,700' }
    ]
  },
  components: {
    SiteHeader,
    ChatBox
  }
}
</script>

<style>

* {
  box-sizing: border-box;
}
body {
  font-size: 16px;
  padding: 0;
  margin: 0;
}
@media only screen and (max-width: 640px) {
  body {
    font-size: 14px;
  }
}
.container {
  max-width: 960px;
  width: 100%;
  margin: 0 auto;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
}

</style>
