<template>
    <nav>
        <img src="public/imagotipo_steam.svg" alt="logo">
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
        <div class="iconos-derecha">
            <div class="nav-iconos">
                <Icon name="ic:outline-search"></Icon>
            </div>
            <div class="icono-perfil">
                <button v-if="!isAuthenticated" @click="$emit('open-login')" class="login-button">Iniciar sesión</button>
                <Icon v-else name="ic:outline-account-circle" @click="toggleProfileModal"></Icon>
            </div> 
        </div>
        <PanelPerfil :isOpen="isProfileModalOpen" @close="toggleProfileModal" />
    </nav>
    
</template>

<script setup>
    import { ref } from 'vue';
    import PanelPerfil from './PanelPerfil.vue'; 
    
    const props = defineProps({
        isAuthenticated: Boolean
    });

    const isProfileModalOpen = ref(false);

    const toggleProfileModal = () => {
        isProfileModalOpen.value = !isProfileModalOpen.value;
    };
</script>

<style lang="postcss">
    nav{
        @apply flex;
        justify-content: space-between;
        align-items: center;
        background-color: #2B2B2B;
        color: #DEDEDE;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 110px;
        z-index: 2000;
        font-size: 24px;
        padding-left: 40px;

    }
    ul{
        @apply flex;
        li{
            padding-left: 40px;
            align-content: center;
        }
    }
    .panel{
        background-color: #2B2B2B;
        width: 300px;
        height: 300px; 
    }
    .active-link {
        font-weight: bold;
        color: #C714E4;
        border-bottom: #C714E4 solid 4px;
    }
    .iconos-derecha{
        padding-right: 40px;
        @apply flex;
        align-items: center;
        .nav-iconos , .icono-perfil{
            font-size: 45px;
            padding-right: 20px;
        }
        .icono-perfil{
            &:hover{
                cursor: pointer;
            }
        }
        .login-button{
            font-size: 25px;
            background-color: transparent;
            border: none;
        }
    }
    
    @media (max-width: 700px) {
        nav{
            max-width: 100%;
            
        }
        ul{
            display: none;
        }
    }
    
</style>