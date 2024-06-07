<template>
  <div v-if="isOpen" class="modal">
    <div class="modal-content">
      <span class="close" @click="$emit('close')">&times;</span>
      <h2>Iniciar sesión</h2>
      <form @submit.prevent="handleLogin">
        <input v-model="emailOrUsername" type="text" placeholder="Introduce tu correo electrónico o nombre de usuario" required>
        <input v-model="password" type="password" placeholder="Introduce tu contraseña" required>
        <button class="iniciar" type="submit">Iniciar sesión</button>
        <button @click="openRegisterModal">Registrarse</button>
      </form>
    </div>
  </div>
</template>

<script>
  import { validEmail, validUsername, validPassword } from './credenciales.js';

  export default {
    props: {
      isOpen: {
        type: Boolean,
        required: true
      }
    },
    data() {
      return {
        emailOrUsername: '',
        password: ''
      };
    },
      methods: {
      handleLogin() {
        if (this.emailOrUsername === validEmail && this.password === validPassword) {
          this.$emit('login-success');
        } else {
          alert('Correo o contraseña incorrectos.');
        }
      },
      openRegisterModal() {
        this.$emit('open-register');
      }
    }
  };
</script>

<style>
  .modal {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 1000;
  }
  .modal-content {
    background: white;
    padding: 20px;
    border-radius: 5px;
    width: 300px;
  }
  .close {
    float: right;
    cursor: pointer;
  }
</style>
