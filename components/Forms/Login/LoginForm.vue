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
            <v-subheader class="login-form-subheader">Email</v-subheader>
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
            <v-subheader class="login-form-subheader">Password</v-subheader>
            <v-text-field
              v-model="password"
              type="password"
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
              <v-checkbox class="login-form-remember" color="#7F56D9" v-model="remember" label="Remember me" hide-details></v-checkbox>
              <nuxt-link class="forgot-password-link" to="#">Forgot password?</nuxt-link>
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
      }
    }
  },
  computed: {
    validEmail() {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return this.email !== '' && emailRegex.test(this.email);
    },
    validPassword() {
      return this.password !== '' && this.password.length >= 8
    }
  }
}
</script>


<style scoped>

* {
 font-family: Inter, sans-serif;
 color: #475467;
 margin: 0;
 padding: 0;
}

html, body {
  height: 100%;
}

.login-form-container {
  padding: 0;
  height: 100vh;
}

.login-form-col {
  background-color: #f1f1f1;
}

.login-image-col {
  padding: 0;
}

.login-image {
  width: auto;
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
@media (min-width: 1150px) {
  .login-form {
    margin-top: 2rem;
  }
}
@media (min-width: 1400px) {
  .login-form {
    margin-top: 5rem;
  }
}
@media (max-width: 360px) {
  .login-form {
    width: 330px;
  }
}
.login-form-logo {
  margin: 15rem auto 0;
}
@media (max-width: 814px) {
  .login-form-logo {
    margin: 8rem auto 0;
  }
}
@media (max-width: 420px) {
  .login-form-logo {
    margin: 10rem auto 0;
  }
}
.login-form-title {
  margin-top: 1.5rem;
  margin-bottom: 2rem;
  text-align: center;
  color: #101828;
}
@media (max-width: 720px) {
  .login-form-title h1{
    font-size: 24px;
  }
}

.login-form-trouble {
  margin-top: 1.5rem;
  text-align: center;
}

.forgot-password-link {
  display: inline-block;
  margin-left: auto;
  font-size: 14px;
}

.login-form-remember label {
  font-size: 14px;
}
.login-form-trouble {
  font-size: 14px;
}
.btn-sign {
  color: #f1f1f1;
  margin-top: 1.5rem;
  font-family: 'Inter',sans-serif;
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 24px;
  text-transform: capitalize;
}

a {
  text-decoration: none;
  color: #6941C6;
  font-weight: 600;
}

.validation-error >>> fieldset {
  border-color: #FDA29B;
}
.login-form-subheader.v-subheader {
  padding: 0;
  color: #344054;
  font-weight: 500;
  font-size: 14px;
  line-height: 20px;
}
.v-input--checkbox::v-deep .v-label, .v-icon {
  font-size: 14px;
  color: #344054;
}

</style>
