<template>
  <div class="signup">
    <section>
      <div class="container">
        <h1>Signup</h1>
        <signup-form class="form"/>
      </div>
    </section>
  </div>
</template>

<script>
import SignupForm from '@/components/SignupForm'

export default {
  name: 'signup',
  components: {
    SignupForm
  }
}
</script>

<style scoped>
:host {
  display: flex;
}
.signup {
  display: flex;
  flex-direction: column;
}
.form {
  max-width: 420px;
}
</style>