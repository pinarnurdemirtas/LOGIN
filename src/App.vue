<template>
  <div class="min-h-screen flex justify-center items-center bg-gray-100">
    <LoginForm v-if="!isLoggedIn" @login-success="handleLoginSuccess" />
    <WelcomeMessage v-else :user="currentUser" />
  </div>
</template>

<script>
import LoginForm from './components/LoginForm.vue';
import WelcomeMessage from './components/WelcomeMessage.vue';

export default {
  components: {
    LoginForm,
    WelcomeMessage
  },
  data() {
    return {
      isLoggedIn: false,
      currentUser: null
    };
  },
  methods: {
    handleLoginSuccess(user) {
      this.isLoggedIn = true;
      this.currentUser = user;
    }
  }
};
</script>


