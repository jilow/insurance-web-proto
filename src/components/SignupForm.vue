<template>
  <div class="signupform">
    <el-form ref="form" :model="form" :rules="rules" label-width="120px">
      <el-form-item label="First name" prop="name">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="Last name" prop="surname">
        <el-input v-model="form.surname"></el-input>
      </el-form-item>
      <el-form-item label="Email Address" prop="email">
        <el-input v-model="form.email"></el-input>
      </el-form-item>
      <el-form-item label="Password" prop="password">
        <el-input v-model="form.password"></el-input>
      </el-form-item>
      <el-form-item label="ID Number" prop="id">
        <el-input v-model="form.id.number"></el-input>
      </el-form-item>
      <el-form-item label="Gender" prop="gender">
        <el-select v-model="form.gender" placeholder="I am...">
          <el-option label="Female" value="female"></el-option>
          <el-option label="Male" value="male"></el-option>
          <el-option label="Other" value="other"></el-option>
          <el-option label="Rather not say" value="unspecified"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit('form')">Signup</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'SignupForm',
  data() {
    return {
      form: {
        name: '',
        surname: '',
        email: '',
        id: {
          type: 'id',
          number: '',
          country: 'ZA'
        },
        password: '',
        gender: 'unspecified'
      },
      rules: {
        name: [
          { required: true, message: 'Please enter your fist name', trigger: 'blur' },
          { min: 1, message: 'Please enter your fist name', trigger: 'blur' }
        ],
        surname: [
          { required: true, message: 'Please enter your last name', trigger: 'blur' },
          { min: 1, message: 'Please enter your last name', trigger: 'blur' }
        ],
        email: [
          { required: true, message: 'Please enter your email address', trigger: 'blur' },
          { type: 'email', message: 'Please input correct email address', trigger: 'blur,change' }
        ],
        password: [
          { required: true, message: 'Please enter your password', trigger: 'blur' },
          { min: 4, message: 'Password must be 4 characters long', trigger: 'blur' }
        ],
        id: [
          { required: true, trigger: 'blur', validator: function(rule, id, cb) {
            if (!id.number) return cb(new Error('Please enter your ID Number'))
            if (!/^[0-9]{13}$/.test(id.number)) return cb(new Error('Please enter a valid ID Number'))
            return cb()
          }}
        ]
      }
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!', this.form)
      axios.post('http://localhost:3000/register-user', {user: this.form})
        .then((res) => {
          console.log(res)
        }).catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<style scoped>

.signupform {

}

* {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}

</style>
