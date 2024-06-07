<template>
  <div v-if="isOpen" class="modal-overlay">
    <div class="modal-content">
      <div class="caja-boton-cerrar">
        <Icon name="ic:baseline-close" class="close-button" @click="closeModal"></Icon>
      </div>
      <div class="caja-apartados">
        <div class="apartados-perfil">
          <Icon class="iconos-perfil" name="ic:outline-shopping-cart"></Icon>
          <h2>Carrito</h2>
        </div>
        <div class="apartados-perfil">
          <Icon class="iconos-perfil" name="ic:baseline-wallet"></Icon>
          <h2>Monedero</h2>
        </div>
        <div class="apartados-perfil">
          <Icon class="iconos-perfil" name="ic:baseline-favorite-border"></Icon>
          <h2>Lista de deseos</h2>
        </div>
        <div class="apartados-perfil">
          <Icon class="iconos-perfil" name="ic:outline-present-to-all"></Icon>
          <h2>Mi Contenido</h2>
        </div>
        <div class="apartados-perfil">
          <Icon class="iconos-perfil" name="ic:twotone-groups"></Icon>
          <h2>Mis Amigos</h2>
        </div>
        <div class="apartados-perfil">
          <Icon class="iconos-perfil" name="ic:outline-workspace-premium"></Icon>
          <h2>Mis Insignias</h2>
        </div>
        <div class="apartados-perfil">
          <Icon class="iconos-perfil" name="ic:baseline-settings"></Icon>
          <h2>Configuración</h2>
        </div>
        <p>Cerrar sesión</p>
        <ul>
          <li>
            <NuxtLink to="/" active-class="active-link">Tienda</NuxtLink>
          </li>
          <li>
            <NuxtLink>Comunidad</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/categorias" active-class="active-link">Categorías</NuxtLink>
          </li>
          <li>
            <NuxtLink>Puntos</NuxtLink>
          </li>
        </ul>
        
      </div>
    </div>
  </div>
</template>

<script setup>
  const props = defineProps({
    isOpen: {
      type: Boolean,
      required: true
    }
  });

  const emit = defineEmits(['close']);

  const closeModal = () => {
    emit('close');
  };    
</script>

<style scoped>
  .modal-overlay {
    position: fixed;
    top: 110px;
    right: 0;
    left: auto;
    width: 300px;
    height: 100vh;
    background: rgba(0, 0, 0, 0);
    z-index: 1000;
    border-top-left-radius: 0;
    border-top-right-radius: 0;
  }
  

  .modal-content {
    background-color: #2b2b2b;
    color: white;
    text-align: center;
    font-weight: 400;
    padding: 20px;
    border-radius: 10px;
    max-width: 300px;
    width: 100%;
    height: 100vh;
  }
  .caja-boton-cerrar{
    display: flex;
    justify-content: flex-end;
    text-align: right;
    position: fixed;
    right: 2%;
  }
  .caja-apartados{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .apartados-perfil{
    display: flex;
    align-items: center;
    text-align: center;
    padding: 20px;
    border-bottom: #C714E4 solid 2px;
    font-size: 18px;
    width: 250px;
    h2{
      padding-left: 15px;
    }
    .iconos-perfil{
      font-size: 30px;
    }
    
  }
  ul{
    display: none;
  }
  p{
      padding-top: 20px;
      color: #C714E4;
      font-weight: 700;
      font-size: 18px;
  }
  @media (max-width: 700px) {
    .modal-overlay{
      max-height: 100vh;
      background-color: #2b2b2b;
    }
    p{
      border-bottom: #C714E4 solid 2px;
      width: 250px;
      padding-bottom: 20px;
    }
    ul{
      display: flex;
      flex-direction: column;
      font-size: 18px;
      width: 250px;
      text-align: left;
      
      li{
        padding-top: 20px;
        padding-bottom: 20px;
        border-bottom: #C714E4 solid 2px;
      }
    }
  }
</style>
