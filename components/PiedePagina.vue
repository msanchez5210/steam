<template>
    <footer>
        <div class="textos-footer">
            <h3 class="titulos-seccion">Acerca de</h3>
            <p>Sobre nosotros</p>
            <p>Trabajos</p>
            <p>Socios de Steam</p>
            <p>Publicaciones</p>
        </div>
        <div class="textos-footer">
            <h3 class="titulos-seccion">Soporte</h3>
            <p>¿En qué podemos ayudarte?</p>
            <p>FAQ</p>
            <p>Información de envío</p>
            <p>Condiciones</p>
            <p>Formulario de contacto</p>
            <p>Política de privacidad</p>
        </div>
        <div class="textos-footer">
            <h3 class="titulos-seccion">Noticias</h3>
            <p>Novedades</p>
            <p>Destacados</p>
            <p>Sorteos</p>
            <p>Próximos juegos</p>
            <p>Lanzamientos recientes</p>
        </div>
        <div class="textos-footer">
            <h3 class="titulos-seccion">Distribución</h3>
            <p>Información</p>
            <p>Normas y directrices</p>
            <p>Inicia sesión para empezar</p>
        </div>
        <div class="iconos-footer">
            <img src="public/logo_steam.svg" alt="Logo Steam">
            <div class="rrss">
                <div class="link-rrss">
                    <img src="public/logo_facebook.svg" alt="Logo Facebook">
                    <NuxtLink to="https://www.facebook.com/Steam/?locale=es_ES">@steam</NuxtLink>
                </div>
                <div class="link-rrss">
                    <img src="public/logo_x.svg" alt="Logo X">
                    <NuxtLink to="https://x.com/Steam?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor">Steam</NuxtLink>
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>

</script>

<style lang="postcss">
    footer{
        background-color: #2b2b2b;
        color: white;
        @apply flex;
        justify-content: space-around;
        padding: 15px;
        
    }
    .textos-footer{
        padding: 30px;
        p{
            font-size: 15px;
            font-weight: 200;
            padding-bottom: 10px;
        }
        .titulos-seccion{
            font-size: 25px;
            font-weight: 500;
            padding-bottom: 15px;
        }
    }
    .iconos-footer{
        padding: 30px;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .rrss{
        @apply flex;
        padding-top: 30px;
        .link-rrss{
            @apply flex;
            padding: 15px;
        }
        img{
            padding-right: 10px;
        }
    }

</style>