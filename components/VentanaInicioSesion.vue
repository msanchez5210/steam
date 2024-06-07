<template>
  <div v-if="isOpen" class="modal">
    <div class="modal-content">
      <div class="caja-boton-cerrar">
        <Icon name="ic:baseline-close" class="close-button" @click="$emit('close')">&times;</Icon>
      </div>
      <div class="bloque-formulario">
        <h2>Iniciar sesión</h2>
        <form @submit.prevent="handleLogin">
          <input v-model="emailOrUsername" type="text" placeholder="Introduce tu correo electrónico o nombre de usuario" required>
          <input v-model="password" type="password" placeholder="Introduce tu contraseña" required>
          <button type="submit">Iniciar sesión</button>
          <p>¿Todavía no tienes una cuenta de Steam?</p>
          <button class="iniciar" @click="openRegisterModal">Regístrate aquí</button>
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
    background-color: #DEDEDE;
    padding: 20px;
    border-radius: 5px;
    width: 200px;
    color: #2b2b2b;
    text-align: center;
  }
  h2{
    font-size: 45px;
    font-weight: 500;
    padding-bottom: 20px;
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
