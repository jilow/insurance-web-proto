<template>
  <main class="home">
    <section class="hero">
      <div class="background"></div>
      <h1>Insurance that works for you.</h1>
    </section>
    <section class="main">
      <div class="container">
        <gadget-list/>
      </div>
    </section>
  </main>
</template>

<script>
import GadgetList from '@/components/GadgetList'

export default {
  name: 'home',
  components: {
    GadgetList
  }
}
</script>

<style scoped>
:host {
  display: flex;
}
.home {
  display: flex;
  flex-direction: column;
}
.hero {
  font-family: 'Quicksand', sans-serif;
  color: #fff;
  display: flex;
  justify-content: center;
  text-align: center;
  align-items: center;
  position: relative;
  min-height: 400px;
  height: 50vh;
}
.hero h1 {
  font-size: 2.4rem;
}
.background {
  position: absolute;
  background-image: url(../assets/hero.jpg);
  background-size: cover;
  background-position: center;
  width: 100%;
  height: 100%;
  z-index: -1;
}
.background:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #414a4f;
  opacity: 0.5;
}
.main {
  margin-top: 2rem;
  margin-bottom: 4rem;
}
</style>