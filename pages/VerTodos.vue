<template>
    <div class="ver-todos-container">
        <h1>Todos los Artículos</h1>
        <section class="contenido">
            <div class="grid-container">
                <div class="grid-item" v-for="(article, index) in paginatedArticles" :key="index">
                    <ArticleCard :article="article" @open-modal="showModal"/>
                </div>
            </div>
            <button @click="loadMore" v-if="canLoadMore">Ver más</button>
        </section>
        <VentanaDetalles :article="selectedArticle" :isOpen="isModalOpen" @close="closeModal" />
    </div>

    <footer>
        <PiedePagina/>
    </footer>
</template>

<script setup>
    import { ref, computed, onMounted } from 'vue';
    import { useRoute } from 'vue-router';
    import ArticleCard from '@/components/ArticleCard.vue';
    import VentanaDetalles from '@/components/VentanaDetalles.vue';

    const route = useRoute();

    const articlesFromIndex = ref([
        { id: 1, title: "STAR WARS Jedi: Survivor", url: "juego1.svg", fullPrice: "31,41€", reducedPrice: "64,50€" },
        { id: 2, title: "Overcooked 2", url: "juego4.jpg", fullPrice: "31,41€", reducedPrice: "64,50€" },
        { id: 3, title: "Bloodborne", url: "juego3.svg", fullPrice: "31,41€", reducedPrice: "64,50€" },
        { id: 4, title: "Rust", url: "juego5.webp", fullPrice: "31,41€", reducedPrice: "64,50€" },
        { id: 5, title: "Elden Ring", url: "juego6.avif", fullPrice: "31,41€", reducedPrice: "64,50€" },
        { id: 6, title: "Warframe", url: "juego7.avif", fullPrice: "31,41€", reducedPrice: "64,50€" },
        { id: 7, title: "Call of Duty: Black Ops III", url: "juego8.jpg", fullPrice: "31,41€", reducedPrice: "64,50€" },
        { id: 8, title: "Red Dead Redemption II", url: "juego9.avif", fullPrice: "31,41€", reducedPrice: "64,50€" }
    ]);

    const articlesFromCategories = ref([
        { id: 9, title: "Dead by Daylight", url: "juego10.jpg", price: "31,41€" },
        { id: 10, title: "Assassin's Creed II", url: "juego11.jpg", price: "31,41€" },
        { id: 11, title: "Monster Hunter World", url: "juego12.avif", price: "31,41€" },
        { id: 12, title: "Overwatch 2", url: "juego13.jpg", price: "31,41€" },
        { id: 13, title: "Palworld", url: "juego14.jpg", price: "31,41€" },
        { id: 14, title: "Far Cry 4", url: "juego15.avif", price: "31,41€" },
        { id: 15, title: "EA SPORTS FC™ 24", url: "juego16.avif", price: "31,41€" },
        { id: 16, title: "Russian Fishing 4", url: "juego17.jpg", price: "31,41€" }
    ]);


    const itemsPerPage = 16;
    const currentPage = ref(1);

    const originalArticles = computed(() => {
        if (route.query.origin === 'categorias') {
            return articlesFromCategories.value;
        } else {
            return articlesFromIndex.value;
        }
    });

    const paginatedArticles = computed(() => {
        const totalItems = currentPage.value * itemsPerPage;
        let articles = [];

        while (articles.length < totalItems) {
            articles = articles.concat(originalArticles.value);
        }

        return articles.slice(0, totalItems);
    });

    const canLoadMore = computed(() => {
        return paginatedArticles.value.length < (originalArticles.value.length * 5); // asumiendo un límite arbitrario de 5 repeticiones
    });

    const loadMore = () => {
        currentPage.value++;
    };
    
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
    .ver-todos-container {
        padding: 110px 20px 100px 20px;
        color: #2b2b2b;
    }
    .contenido {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    h1 {
        font-size: 45px;
        font-weight: 400;
        padding-bottom: 25px;
    }
    .grid-container {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 20px;
        margin-bottom: 35px;
    }
    .grid-item {
        background: white;
        border-radius: 40px;
    }
    button {
        margin-top: 20px;
        padding: 10px 40px;
        background-color: white;
        color: #C714E4;
        font-weight: 700;
        border: #C714E4 solid 2px;
        border-radius: 40px;
        cursor: pointer;
    }
    @media (max-width: 700px) {
        .grid-container {
            display: flex;
            flex-direction: column;
        }
    }
    @media (max-width: 800px) {
        .grid-container {
            grid-template-columns: repeat(2, 1fr);
        }
    }
    @media (max-width: 1205px) {
        .grid-container {
            grid-template-columns: repeat(3, 1fr);
        }
    }
</style>
