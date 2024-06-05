<template>
    <main>
        <section class="main-section">
            <div class="titulos-apartados">
                <h3>Acción</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'categorias' }}" class="vertodos">Ver todos</NuxtLink>
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
                <h3>Juegos de rol</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'categorias' }}" class="vertodos">Ver todos</NuxtLink>
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
                <h3>Arcade</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'categorias' }}" class="vertodos">Ver todos</NuxtLink>
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
                <h3>Aventura</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'categorias' }}" class="vertodos">Ver todos</NuxtLink>
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
                <h3>Estrategia</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'categorias' }}" class="vertodos">Ver todos</NuxtLink>
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
                <h3>Deportes</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'categorias' }}" class="vertodos">Ver todos</NuxtLink>
            </div>  
            <div class="swiper-container">
                <div class="swiper-wrapper">
                    <div class="swiper-slide" v-for="(article, index) in articles" :key="index">
                        <ArticleCard :article="article" @open-modal="showModal"/>
                    </div>
                </div>
                <div class="swiper-button-next"></div>                    
            </div>
            <div class="titulos-apartados">
                <h3>Simulación</h3>
                <NuxtLink :to="{ path: '/VerTodos', query: { origin: 'categorias' }}" class="vertodos">Ver todos</NuxtLink>
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
    
    const articles = ref([
        {
            id: 1,
            title: "Dead by Daylight",
            url: "juego10.jpg",
            price: "7,99€",
            precioDeluxe: "34,79€",
            precioPremium: "46,07€",
            descripcion: "Dead by Daylight es un juego de horror de multijugador (4 contra 1) en el que un jugador representa el rol del asesino despiadado y los 4 restantes juegan como supervivientes que intentan escapar de él para evitar ser capturados, torturados y asesinados. Los supervivientes juegan en tercera persona y tienen la ventaja de contar con una mejor percepción del entorno. El asesino juega en primera persona y está más enfocado en su presa. El objetivo del superviviente en cada encuentro es escapar del área de matanza sin que lo capture el asesino, algo que suena más fácil de lo que es, especialmente con un entorno que cambia cada vez que juegas."
        },
        {
            id: 2,
            title: "Assassin's Creed II",
            url: "juego11.jpg",
            price: "9,99€",
            precioDeluxe: "18,99€",
            precioPremium: "424,86€",
            descripcion: "Assassin's Creed® 2 es la secuela del título que se convirtió en la nueva IP con unas ventas más rápidas de la historia de los videojuegos. Este título tan largamente esperado introduce a un nuevo héroe, Ezio Auditore da Firenze, un joven noble italiano, y una nueva era, el Renacimiento. Assassin's Creed 2 es una historia épica de familia, venganza y conspiración que tiene lugar en el prístino, aunque brutal, trasfondo de una Italia renacentista. Ezio entabla amistad con Leonardo da Vinci, se enfrenta con las familias más poderosas de Florencia y se aventura por los canales de Venecia donde aprende a ser un maestro asesino."
        },
        {
            id: 3,
            title: "Monster Hunter: World",
            url: "juego12.avif",
            price: "9,89€",
            precioDeluxe: "19,79€",
            precioPremium: "24,79€",
            descripcion: "¡Bienvenidos a un nuevo mundo! Conviértete en un gran cazador y acaba con feroces monstruos en un ecosistema lleno de vida donde podrás aprovechar tu entorno y su variada flora y fauna para vencer. ¡Caza solo o en cooperativo con hasta tres jugadores más y usa los materiales abandonados por tus enemigos caídos para crear nuevo equipo con que luchar con bestias aún más grandes y poderosas!"
        },
        {
            id: 4,
            title: "Overwatch 2",
            url: "juego13.jpg",
            price: "Gratis",
            precioDeluxe: "14,99€",
            precioPremium: "39,99€",
            descripcion: "¡Bienvenidos a un nuevo mundo! Conviértete en un gran cazador y acaba con feroces monstruos en un ecosistema lleno de vida donde podrás aprovechar tu entorno y su variada flora y fauna para vencer. ¡Caza solo o en cooperativo con hasta tres jugadores más y usa los materiales abandonados por tus enemigos caídos para crear nuevo equipo con que luchar con bestias aún más grandes y poderosas!"
        },
        {
            id: 5,
            title: "Palworld",
            url: "juego14.jpg",
            price: "28,99€",
            precioDeluxe: "33,14€",
            precioPremium: "48,14€",
            descripcion: "Este es un juego multijugador de supervivencia en mundo abierto inmenso y original, en el que tendrás que hacerte con unas misteriosas criaturas llamadas Pals, capaces de combatir, construir, cultivar y trabajar en fábricas."
        },
        {
            id: 6,
            title: "Far Cry 4",
            url: "juego15.avif",
            price: "5,99€",
            precioDeluxe: "14,99€",
            precioPremium: "175,41€",
            descripcion: "Oculto en la recóndita cordillera del Himalaya se encuentra Kyrat, un país anclado en la tradición y la violencia. Eres Ajay Ghale. Viajarás a Kyrat para cumplir con el último deseo de tu madre, pero una vez allí te verás atrapado en una guerra civil desatada para acabar con el régimen opresivo del dictador Pagan Min. Explora y navega este gigantesco mundo de juego, en el que el peligro y los imprevistos acechan a la vuelta de cualquier esquina. Cada decisión que tomes aquí cuenta, y cada segundo es una historia. Bienvenido a Kyrat."
        },
        {
            id: 7,
            title: "EA SPORTS FC™ 24",
            url: "juego16.avif",
            price: "39,99€",
            precioDeluxe: "69,99€",
            precioPremium: "99,99€",
            descripcion: "EA SPORTS FC™ 24 te da la bienvenida a The World's Game: la experiencia futbolística más fiel hasta la fecha con HyperMotionV, PlayStyles optimizado por Opta y el motor mejorado de Frostbite™."
        },
        {
            id: 8,
            title: "Russian Fishing 4",
            url: "juego17.jpg",
            price: "Gratis",
            precioDeluxe: "Gratis",
            precioPremium: "Gratis",
            descripcion: "Russian Fishing 4 es un simulador de pesca con elementos de RPG. No hay una trama y todo el proceso se basa en el concepto de un juego abierto, gratuito y gratuito."
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