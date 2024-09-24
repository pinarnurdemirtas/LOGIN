<template>
    <div class="min-h-screen flex items-center justify-center">
      <div class="bg-white p-8 rounded-lg shadow-lg max-w-lg w-full"> <!-- max-w-md yerine max-w-lg -->
        <h2 class="text-4xl font-extrabold text-center text-gray-800 mb-8">
          Giriş Yap
        </h2>
        <form class="space-y-6" @submit.prevent="login">
          <div>
            <label class="block text-gray-700 text-lg mb-2">Kullanıcı Adı</label>
            <input
              v-model="username"
              type="text"
              placeholder="Kullanıcı adınızı girin"
              class="w-full px-4 py-3 border border-gray-300 rounded-lg bg-gray-50 focus:outline-none focus:ring-4 focus:ring-blue-500"
              required
            />
          </div>
          <div>
            <label class="block text-gray-700 text-lg mb-2">Şifre</label>
            <input
              v-model="password"
              type="password"
              placeholder="Şifrenizi girin"
              class="w-full px-4 py-3 border border-gray-300 rounded-lg bg-gray-50 focus:outline-none focus:ring-4 focus:ring-blue-500"
              required
            />
          </div>
          <p v-if="errorMessage" class="text-red-500">{{ errorMessage }}</p>
          <button
            type="submit"
            class="bg-purple-950 text-white px-6 py-3 rounded-lg hover:bg-purple-800 focus:outline-none w-full"
            :disabled="loading"
          >
            {{ loading ? 'Giriş Yapılıyor...' : 'Giriş Yap' }}
          </button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        errorMessage: '',
        loading: false
      };
    },
    methods: {
      login() {
        this.loading = true;
        const users = [
          { username: 'Pınar', password: '123' },
          { username: 'Nur', password: '456' }
        ];
        const user = users.find(
          u => u.username === this.username && u.password === this.password
        );
        setTimeout(() => {
          if (user) {
            this.$emit('login-success', user);
            this.errorMessage = '';
          } else {
            this.errorMessage = 'Kullanıcı adı veya şifre yanlış.';
          }
          this.loading = false;
        }, 500); // Simulate API request delay
      }
    }
  };
  </script>
  
  