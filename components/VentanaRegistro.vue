<template>
  <div v-if="isOpen" class="modal">
    <div class="modal-content">
      <span class="close" @click="$emit('close')">&times;</span>
      <h2>Registro</h2>
      <form @submit.prevent="handleRegister">
        <input v-model="email" type="email" placeholder="Introduce un correo electrónico" required>
        <input v-model="username" type="text" placeholder="Crea un nombre de usuario" required>
        <input v-model="password" type="password" placeholder="Introduce una contraseña" required>
        <button type="submit">Registrarse</button>
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
        email: '',
        username: '',
        password: ''
      };
    },
    methods: {
      handleRegister() {
        if (this.email === validEmail && this.username === validUsername && this.password === validPassword) {
          this.$emit('register-success');
        } else {
          alert('Datos de registro incorrectos.');
        }
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
