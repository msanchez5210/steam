<template>
  <div v-if="isOpen" class="modal">
    <div class="modal-content">
      <div class="caja-boton-cerrar">
        <Icon name="ic:baseline-close" class="close-button" @click="$emit('close')">&times;</Icon>
      </div>
      <div class="bloque-formulario">
        <h2>Registro</h2>
        <form @submit.prevent="handleRegister">
          <input v-model="email" type="email" placeholder="Introduce un correo electrónico" required>
          <input v-model="username" type="text" placeholder="Crea un nombre de usuario" required>
          <input v-model="password" type="password" placeholder="Introduce una contraseña" required>
          <button type="submit">Registrarse</button>
          <p>¿Ya tienes una cuenta de Steam?</p>
          <button class="iniciar" @click="openLoginModal">Inicia sesión aquí</button>
        </form>
      </div>
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
      },
      openLoginModal() {
        this.$emit('close');
        this.$emit('open-login');
      },
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
  .bloque-formulario{
    display: flex;
    flex-direction: column;
    align-items: center;
    form{
      display: flex;
      flex-direction: column;
      max-width: 500px;
      width: 100%;
      input{
        margin-bottom: 10px;
        background-color: white;
        color: #2b2b2b;
        padding: 20px;
        border-radius: 40px;
        font-size: 14x;
      }
      p{
        padding-top: 20px;
      }
      .iniciar{
        border: none;
        background-color: transparent;
        padding: 0;
        margin: 0;
      }
    }
  }
</style>
