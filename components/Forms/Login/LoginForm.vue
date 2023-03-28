<template>
  <v-container fluid class="login-container">
    <v-row class="fill-height">
      <v-col cols="12" md="6" class="login-form-col fill-height">
        <div class="login-form">
          <div class="login-form-logo">
            <v-img :src="require('~/static/logo.svg')" width="48" height="36" />
          </div>
          <div class="login-form-text">
            <h1>Log in to your account</h1>
          </div>
          <v-form>
            <v-text-field
              v-model="email"
              placeholder="name@hoteldomain.com"
              :error="!validEmail"
              :error-messages="validEmail ? [] : ['Please check email address']"
              :append-icon="validEmail ? undefined : 'mdi-alert-circle-outline'"
              outlined
              :class="{
                'error-field': !validEmail,
                'v-text-field--outlined': true,
                'validation-error': !validEmail,
              }"
            ></v-text-field>
            <v-text-field
              v-model="password"
              placeholder="••••••••"
              :error="!validPassword"
              :error-messages="validPassword ? [] : ['Please fill in your password']"
              :append-icon="validPassword ? undefined : 'mdi-alert-circle-outline'"
              outlined
              :class="{
                'error-field': !validPassword,
                'v-text-field--outlined': true,
                'validation-error': !validPassword,
              }"
            ></v-text-field>
            <div style="display: flex; align-items: center;">
              <v-checkbox color="#7F56D9" v-model="remember" label="Remember me" hide-details>
                Remember me
              </v-checkbox>
              <nuxt-link style="margin-top: 1.2rem" class="forgot-password-link" to="#">Forgot password?</nuxt-link>
            </div>
            <v-btn class="btn-sign" color="#6941C6" width="100%" type="submit" @click.prevent="signin">Sign in</v-btn>
          </v-form>

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
  name: "LoginForm",
  data() {
    return {
      email: '',
      password: '',
      remember: false,

    }
  },
  computed: {
    validEmail() {
      return this.email === '' || this.email.includes('@')
    },
    validPassword() {
      return this.password === '' || this.password.length >= 8
    }
  },
}
</script>

<style scoped>

* {
 font-family: Inter, sans-serif;
}
.fill-height {
  height: 100vh;
}

.login-container {
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
  .login-image {
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

.login-form-text {
  margin-top: 1.5rem;
  margin-bottom: 2rem;
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
