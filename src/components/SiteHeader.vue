<template>
  <header>
    <div class="container nav">
      <router-link to="/" class="home">
        <h2>Insurance Proto</h2>
      </router-link>
      <div class="actions">
        <router-link to="/signup">
          <el-button type="primary">Sign up</el-button>
        </router-link>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'SiteHeader',
  data () {
    return {
    }
  }
}
</script>

<style scoped>

header {
  height: 4rem;
  display: flex;
  background-color: #fff;
  border-bottom: 1px solid #ccc;
}
.nav {
  display: flex;
  align-content: left;
  align-items: center;
  justify-content: space-between;
}
.menu-item {
  cursor: pointer;
  color: #888;
  height: 100%;
  padding: 12px 20px;
}
.menu-item:hover {
  color: #333;
}
.home {
  text-decoration: none;
  font-family: 'Quicksand', sans-serif;
  margin: 0;
}
.actions * {
  text-transform: uppercase;
}
.borderless {
  border: none;
}

</style>
