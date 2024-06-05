<template>
    <article class="swiper-slide" @click="openModal">
      <img :src="article.url" :alt="article.title">
      <div class="article-content">
        <h3>{{ article.title }}</h3>
        <div class="article-info">
          <div class="article-iconos">
            <div class="icon-carrito">
              <Icon name="ic:outline-shopping-cart"></Icon>
            </div>
            <div class="icon-favorito">
              <Icon name="ic:baseline-favorite-border"></Icon>
            </div>
          </div>
          <div class="precios">
            <p class="price-original">{{ article.fullPrice }}</p>
            <p class="price-reduced">{{ article.reducedPrice }}</p>
            <p class="price-reduced">{{ article.price }}</p>
          </div>
        </div>
      </div>
    </article>
</template>

<script setup>
    const props = defineProps({
        article: {
            type: Object,
            required: true
        }
    });

    const emit = defineEmits(['open-modal']);

    const openModal = () => {
        emit('open-modal', props.article);
    };
</script>

<style lang="postcss">
    .swiper-slide {
      background-color: white;
      border-radius: 40px;
      width: 100%;
      cursor: pointer;
      position: relative;
      &:hover{
        background-color: #c714e4;
        color: white;
        border-bottom-left-radius: 40px;
        border-bottom-right-radius: 40px;
      }

      img {
          width: 100%;
          height: 350px;
          object-fit: cover;
          border-top-left-radius: 40px;
          border-top-right-radius: 40px;
      }
      .article-content {
        padding: 20px;
        max-height: 100vh;
        h3 {
          font-size: 20px;
          font-weight: 600;
          padding: 0;
        }
      }
      .article-info {
        @apply flex;
        align-items: baseline;
        justify-content: space-between;
        padding-top: 10px;
        font-size: 15px;
        .article-iconos {
          @apply flex;
          font-size: 30px;
        }
        .precios {
          @apply flex;
          align-items: baseline;
          padding: 0;
        }
        .price-original {
          text-decoration: line-through;
          padding-right: 15px;
        }
        .price-reduced {
          font-size: 25px;
          font-weight: 700;
          color: #c714e4;
          &:hover{
            color: white;
          }
        }
      }
    }
    @media (max-width: 581px) {
        main{
            width:100%;
        }
        .swiper-slide {
          @apply flex;
          img{
            border-radius: 40px;
          }
        }
        .article-content{
          display: flex;
          flex-direction: column;
          justify-content: center;
          .article-info{
            display: flex;
            flex-direction: column;
          }
        }
        
    }
    @media (max-width: 700px) {
        main{
            width:100%;
        }
        .swiper-slide {
          @apply flex;
          img{
            border-radius: 40px;
          }
        }
        .article-content{
          display: flex;
          flex-direction: column;
          justify-content: center;
          .article-info{
            display: flex;
            flex-direction: column;
            .precios{
              display: flex;
              flex-direction: column;
            }
          }
        }
        
    }
</style>
  