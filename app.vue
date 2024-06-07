<template>
  <div id="app">
    <BarraNav :isAuthenticated="isAuthenticated" @open-login="openLogin" @open-register="openRegister" />
    <VentanaInicioSesion :isOpen="isLoginOpen" @close="closeLogin" @login-success="handleLoginSuccess" @open-register="openRegister"  />
    <VentanaRegistro :isOpen="isRegisterOpen" @close="closeRegister" @register-success="handleRegisterSuccess" @open-login="openLogin"/>
    <NuxtPage />
  </div>
</template>

<script>
  import { ref } from 'vue';
  import BarraNav from '@/components/BarraNav.vue';
  import VentanaInicioSesion from '@/components/VentanaInicioSesion.vue';
  import VentanaRegistro from '@/components/VentanaRegistro.vue';

  export default {
    components: {
      BarraNav,
      VentanaInicioSesion,
      VentanaRegistro
    },
    data() {
      return {
        isLoginOpen: ref(false),
        isRegisterOpen: ref(false),
        isAuthenticated: ref(false)
      };
    },
    methods: {
      openLogin() {
        this.isLoginOpen = true;
        this.isRegisterOpen = false;
      },
      closeLogin() {
        this.isLoginOpen = false;
      },
      handleLoginSuccess() {
        this.isAuthenticated = true;
        this.closeLogin();
      },
      openRegister() {
        this.isRegisterOpen = true;
        this.isLoginOpen = false;
      },
      closeRegister() {
        this.isRegisterOpen = false;
      },
      handleRegisterSuccess() {
        this.isAuthenticated = true;
        this.closeRegister();
        this.closeLogin();
      },

    }
  };
</script>

<style>
  body{
    background-color: #DEDEDE;
  }
</style>
