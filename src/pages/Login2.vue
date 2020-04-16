<template>
  <div id="app">
    <div class="container my-4">
      <div class="row justify-content-center">
        <div class="col-md-8">
          <h2 class="text-center mb-4">
            Sign Up Form
          </h2>
          
          <form
              method="post"
              @submit.prevent="validate">
            <div class="form-group">
              <input 
                   type="email" 
                   name="email" 
                   class="form-control" 
                   placeholder="Enter your e-mail address"
                   required />
            </div>
            <div class="form-group">
              <input 
                   type="password" 
                   name="password" 
                   class="form-control" 
                   placeholder="Enter your password"
                   required />                   
            </div>
            <div class="form-group">
              <vue-recaptcha
                ref="recaptcha"
                :sitekey="sitekey"
                @verify="register"
                @expired="onCaptchaExpired"
              />
              <button 
                    type="submit"
                    :disabled="!captureValid"
                    class="btn btn-primary btn-block">
                Sign Up
              </button>
              <button 
                    type="home"
                    @click="home"
                    class="btn btn-primary btn-block">                    
                Home
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueRecaptcha from 'vue-recaptcha'
import MainFooter from '@/layout/MainFooter';

export default {
  name: 'Register',

  components: { 
      VueRecaptcha,
      MainFooter
 },

  data () {
    return {
      email: null,
      password: null,
      sitekey: '6Lf6OekUAAAAAH7gck2HVL1048q9ern43bPwFCJC',
      captureValid: false
    }
  },

  methods: {
    register (recaptchaToken) {
      console.log('register: ', 'email:', this.email, 'this.password: ', this.password, 'recaptchaToken', recaptchaToken)
      this.captureValid = true
      console.log('register: this.captureValid: ', this.captureValid)
    },

    validate () {
      console.log('validate: this.captureValid: ', this.captureValid)
      // тут можно добавить проверку на валидацию
      // например, с помощью vee validate
      // если с валидацией наших полей все хорошо, запускаем каптчу
      // this.$refs.recaptcha.execute()
      if (this.captureValid == true)
      {
        alert("Functionality is under construction...")
      } else {
        alert("Plesse check the box!")
      }
    },

    onCaptchaExpired () {
      console.log('onCaptchaExpired')
      this.captureValid = false
      this.$refs.recaptcha.reset()
      console.log('onCaptchaExpired: this.captureValid: ', this.captureValid)
    },
    home () {
      console.log('home')
      this.$router.push({name: 'index'})
    }
  }
}
</script>