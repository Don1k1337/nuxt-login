<template>
  <v-container fluid class="login-form-container">
    <v-row class="fill-height">
      <v-col cols="12" md="6" class="login-form-col fill-height">
        <div class="login-form">
          <div class="login-form-logo">
            <v-img :src="require('~/static/logo.svg')" width="48" height="36" />
          </div>
          <div class="login-form-title">
            <h1>Log in to your account</h1>
          </div>
          <v-form @submit.prevent="submitForm">
            <v-text-field
              v-model="email"
              placeholder="name@hoteldomain.com"
              :error="!validEmail && formSubmitted"
              :error-messages="validEmail || !formSubmitted ? [] : ['Please check email address']"
              :append-icon="validEmail || !formSubmitted ? undefined : 'mdi-alert-circle-outline'"
              outlined
              :class="{
                'v-text-field--outlined': true,
                'validation-error': !validEmail && formSubmitted,
              }" />
            <v-text-field
              v-model="password"
              placeholder="••••••••"
              :error="!validPassword && formSubmitted"
              :error-messages="validPassword || !formSubmitted ? [] : ['Please fill in your password']"
              :append-icon="validPassword || !formSubmitted ? undefined : 'mdi-alert-circle-outline'"
              outlined
              :class="{
                'v-text-field--outlined': true,
                'validation-error': !validPassword && formSubmitted,
              }"
            ></v-text-field>
            <div style="display: flex; align-items: center;">
              <v-checkbox color="#7F56D9" v-model="remember" label="Remember me" hide-details>
                Remember me
              </v-checkbox>
              <nuxt-link style="margin-top: 1.2rem" class="forgot-password-link" to="#">Forgot password?</nuxt-link>
            </div>
            <v-btn class="btn-sign" color="#6941C6" width="100%" type="submit" @submit.prevent="submitForm">Sign in</v-btn>
          </v-form>
          <div class="login-form-trouble">
            <span class="login-trouble">Can’t log in to your account?</span>
            <nuxt-link to="#">Ask support</nuxt-link>
          </div>
        </div>
      </v-col>
      <v-col cols="12" md="6" class="login-image-col fill-height">
        <v-img
          :src="require('~/static/background-login.svg')"
          alt="Login Image"
          class="login-image fill-height"
          style="object-fit: cover;"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      remember: false,
      formSubmitted: false
    }
  },
  methods: {
    submitForm() {
      this.formSubmitted = true
      if (this.validEmail && this.validPassword) {
        // just for checks
        alert('Submitted')
      } else {
        // just for checks
        alert('Pls, check validation errors')
      }
    }
  },
  computed: {
    validEmail() {
      return this.email !== '' || this.email.includes('@')
    },
    validPassword() {
      return this.password !== '' || this.password.length >= 8
    }
  }
}
</script>


<style scoped>

* {
 font-family: Inter, sans-serif;
 color: #475467;
}

.fill-height {
  height: 100vh;
}

.login-form-container {
  padding: 0;
}

.login-form-col {
  background-color: #f1f1f1;
}

.login-image-col {
  padding: 0;
}

.login-image {
  width: 100%;
}
@media (max-width: 820px) {
  .login-image-col {
    display: none;
  }
}
.login-form {
  width: 360px;
  height: 454px;
  margin: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.login-form-logo {
  margin: 15rem auto 0;
}

.login-form-title {
  margin-top: 1.5rem;
  margin-bottom: 2rem;
  text-align: center;
  color: #101828;
}

.login-form-trouble {
  margin-top: 1.5rem;
  text-align: center;
}

.forgot-password-link {
  display: inline-block;
  margin-left: auto;
}
.btn-sign {
  color: #f1f1f1;
  margin-top: 1.5rem;
  font-weight: 600;
}

a {
  text-decoration: none;
  color: #6941C6;
  font-weight: 600;
}

.validation-error >>> fieldset {
  border-color: #FDA29B;
}

</style>
