<template>
    <main>
        <section class="carruselPrincipal">
            <CarruselPrincipal/>
        </section>
        <section class="main-section">
            <h1>{{ title }}</h1>
            
            <div class="fotosConsolas">
                <img src="public/promo1.jpg" alt="">
                <img src="public/promo2.jpg" alt="">
            </div>

            <div class="titulos-apartados">
                <h3>Destacados</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'index' }}" class="vertodos">Ver todos</NuxtLink>
            </div>
            <div class="swiper-container">
                <div class="swiper-button-prev"></div>
                <div class="swiper-wrapper">
                    <div class="swiper-slide" v-for="(article, index) in articles" :key="index">
                        <ArticleCard :article="article" @open-modal="showModal"/>
                    </div>
                </div>
                <div class="swiper-button-next"></div>                    
            </div>
            <div class="titulos-apartados">
                <h3>Juegos gratuitos</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'index' }}" class="vertodos">Ver todos</NuxtLink>
            </div>            
            <div class="swiper-container">
                <div class="swiper-button-prev"></div>
                <div class="swiper-wrapper">
                    <div class="swiper-slide" v-for="(article, index) in articles" :key="index">
                        <ArticleCard :article="article" @open-modal="showModal"/>
                    </div>
                </div>
                <div class="swiper-button-next"></div>                    
            </div>
            <div class="titulos-apartados">
                <h3>Lo más vendido</h3>
                <NuxtLink class="vertodos">Ver todos</NuxtLink>
            </div>  
            <div class="swiper-container">
                <div class="swiper-button-prev"></div>
                <div class="swiper-wrapper">
                    <div class="swiper-slide" v-for="(article, index) in articles" :key="index">
                        <ArticleCard :article="article" @open-modal="showModal"/>
                    </div>
                </div>
                <div class="swiper-button-next"></div>                    
            </div>
            <div class="titulos-apartados">
                <h3>Juegos transmitidos ahora</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'index' }}" class="vertodos">Ver todos</NuxtLink>
            </div>  
            <div class="swiper-container">
                <div class="swiper-button-prev"></div>
                <div class="swiper-wrapper">
                    <div class="swiper-slide" v-for="(article, index) in articles" :key="index">
                        <ArticleCard :article="article" @open-modal="showModal"/>
                    </div>
                </div>
                <div class="swiper-button-next"></div>                    
            </div>
            <VentanaDetalles :article="selectedArticle" :isOpen="isModalOpen" @close="closeModal" />
        </section>
    </main>

    <footer>
        <PiedePagina/>
    </footer>

</template>

<script setup>
    import { ref } from "vue";
    import Swiper from 'swiper';
    import VentanaDetalles from '@/components/VentanaDetalles.vue';
    
    const title = ref('Bienvenid@ a Steam');
    const articles = ref([
        {
            id: 1,
            title: "STAR WARS Jedi: Survivor",
            url: "juego1.svg",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion:`La historia de Cal Kestis continúa en Star Wars Jedi: Survivor™, un juego de acción y aventuras en tercera persona desarrollado por Respawn Entertainment en colaboración con Lucasfilm Games. Este título para un jugador centrado en la historia retoma la aventura 5 años después de los acontecimientos de Star Wars Jedi: Fallen Order™ y sigue la lucha cada vez más desesperada de Cal mientras la galaxia se hunde en la oscuridad. Empujado al exilio por culpa del Imperio, deberá guardarse de nuevas y viejas amenazas. Como uno de los últimos Caballeros Jedi, debe hacer frente a los tiempos más oscuros de la galaxia, pero ¿hasta dónde está dispuesto a llegar para protegerse a sí mismo, a su tripulación y al legado de la Orden Jedi?`
        },
        {
            id: 2,
            title: "Overcooked 2",
            url: "juego4.jpg",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion: "¡Overcooked vuelve con un nuevo y caótico juego de cocina en acción! Regresa al Reino de la Cebolla y organiza tu equipo de chefs en un cooperativo clásico o en partidas en línea de hasta cuatro jugadores. Agarraos los delantales... es hora de salvar el mundo (¡otra vez!)"
        },
        {
            id: 3,
            title: "Bloodborne",
            url: "juego3.svg",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion: "Da caza a tus pesadillas. Un viajero solitario. Un pueblo maldito. Un misterio letal que devora todo lo que toca. Enfréntate a tus miedos y adéntrate en la ciudad en ruinas de Yharnam, un lugar abandonado asolado por una terrible enfermedad que lo consume todo. Examina sus sombras más oscuras, lucha por tu vida con armas de filo y de fuego, y descubre secretos que harán que se te hiele la sangre... pero que podrían salvarte el pellejo..."
        },
        {
            id: 4,
            title: "Rust",
            url: "juego5.webp",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion: "El único objetivo en Rust es sobrevivir. Todo quiere que mueras: la vida salvaje de la isla y otros habitantes, el medio ambiente y otros supervivientes. Haz lo que sea necesario para durar una noche más."
        },
        {
            id: 5,
            title: "Elden Ring",
            url: "juego6.avif",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion: "Recorre las Tierras Intermedias, un nuevo mundo de fantasía ideado por Hidetaka Miyazaki, creador de la exitosa serie de videojuegos DARK SOULS, y por George R. R. Martin, autor de Canción de hielo y fuego, la serie de fantasía superventas según The New York Times. Desvela los misterios del poder del Círculo de Elden. Enfréntate a criaturas temibles y conoce a adversarios con pasados tumultuosos y personajes con sus propias motivaciones para ayudarte a avanzar o complicarte las cosas. "
        },
        {
            id: 6,
            title: "Warframe",
            url: "juego7.avif",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion: "Despierta como un guerrero imparable y lucha junto a tus amigos en este juego de acción gratuito en línea y basado en historias. Enfréntate a las facciones en guerra en un extenso sistema interplanetario bajo la guía de la misteriosa Lotus, mejora tu warframe, construye un arsenal destructivo y descubre tu verdadero potencial en los enormes mundos abiertos de esta emocionante experiencia de combate en tercera persona que define el género."
        },
        {
            id: 7,
            title: "Call of Duty: Black Ops III",
            url: "juego8.jpg",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion: "Bienvenidos a Call of Duty: Black Ops 3, un futuro oscuro y retorcido en el que nace una nueva raza de soldados Black Ops y en el que se difuminan las líneas entre nuestra propia humanidad y la tecnología que creamos para estar a la vanguardia, en un mundo en el que la robótica militar punta define la guerra. Call of Duty: Black Ops 3 combina tres modos únicos de juego: Campaña, Multijugador y Zombies, proporcionando a los fans el Call of Duty más profundo y ambicioso creado hasta la fecha."
        },
        {
            id: 8,
            title: "Red Dead Redemption II",
            url: "juego9.avif",
            fullPrice: "64,50€",
            reducedPrice:"31,21€",
            precioDeluxe: "45,30€",
            precioPremium: "61,60€",
            descripcion: "América, 1899. Arthur Morgan y la banda de Van der Linde se ven obligados a huir. Con agentes federales y los mejores cazarrecompensas de la nación pisándoles los talones, la banda deberá atracar, robar y luchar para sobrevivir en su camino por el escabroso territorio del corazón de América. Mientras las divisiones internas aumentan y amenazan con separarlos a todos, Arthur deberá elegir entre sus propios ideales y la lealtad a la banda que lo vio crecer."
        }
        
    ]);
    onMounted(() => {
        new Swiper('.swiper-container', {
            slidesPerView: 1,
            spaceBetween: 20,
            navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
            },
            breakpoints: {
            700: {
                slidesPerView: 2,
            },
            800: {
                slidesPerView: 3,
            },
            1080: {
                slidesPerView: 4,
            },
            1205: {
                slidesPerView: 5,
            },
            },
        });
    });
    const isModalOpen = ref(false);
    const selectedArticle = ref({});

    const showModal = (article) => {
        selectedArticle.value = article;
        isModalOpen.value = true;
    };

    const closeModal = () => {
        isModalOpen.value = false;
    };
</script>

<style lang="postcss">
    main{
        width: 100%;
        background-color: #DEDEDE;
        color: #2B2B2B;
        padding-bottom: 100px;
        padding-top: 110px;
    }
    .swiper-container{
        position: relative;
        overflow: hidden;
        max-width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
    }
    .swiper-wrapper{
        display: flex;
    }
    .cards-section{
        display: flex;
        justify-content: space-between;
    }
    .main-section{
        padding: 20px;
        h1{
        font-size: 45px;
        color: rgb(43, 43, 43);
        padding-top: 20px;
        padding-bottom: 20px;
        }
        h3{
            font-size: 30px;
            padding-bottom: 25px;
            padding-top: 43px;
        }
    }
    .titulos-apartados{
        @apply flex;
        align-items: baseline;
        justify-content: space-between;
    }
    .fotosConsolas{
        @apply flex;
        justify-content: center; 
        height: 140px;
        overflow: hidden; 
        width: 100%; 
        img{
            width: 100%; 
            height: auto;
            object-fit: cover; 
        }
    }
    .vertodos{
        color: #2B2B2B;
        &:hover{
            color: #C714E4;
            cursor: pointer;
        }
    }
    @media (max-width: 581px) {
        main{
            width:100%;
        }
        .fotosConsolas{
            display: flex;
            flex-direction: column;
            height: auto;
            width: 100%;
        }
        .swiper-slide {
            @apply flex;
        }
    }
    
</style>