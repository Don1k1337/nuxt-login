<template>
  <login-form />
</template>

<script>
import LoginForm from "../components/Forms/Login/LoginForm.vue";

export default {
  name: "login",
  components: {LoginForm}
}
</script>


<style>
.error--text{
  color: #dc3131 !important;
}
</style>
