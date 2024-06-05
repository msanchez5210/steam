<template>
  <div v-if="isOpen" class="modal-overlay" @click.self="closeModal">
    <div class="modal-content">
      <div class="arriba">
        <h2>{{ article.title }}</h2>
        <Icon name="ic:baseline-close" class="close-button" @click="closeModal">&times;</Icon>
      </div>
      <div class="medio">
        <img :src="article.url" :alt="article.title">
        <div class="caja-precios">
          <div class="precios">
            <div class="boton-precios1">
              <p>Comprar juego base</p>
              <p class="cantidad" v-if="article.reducedPrice"> {{ article.reducedPrice }}</p>
              <p class="cantidad" v-if="article.price">{{ article.price }}</p>
            </div>
            <div class="boton-precios2">
              <p>Comprar Deluxe Edition</p>
              <p class="cantidad" v-if="article.precioDeluxe">{{ article.precioDeluxe }}</p>
            </div>
            <div class="boton-precios2">
              <p>Comprar Bundle Pack</p>
              <p class="cantidad" v-if="article.precioPremium">{{ article.precioPremium }}</p>
            </div>
          </div>
          <div class="caja-iconos">
            <div class="iconos">
              <Icon name="ic:outline-shopping-cart"></Icon>
            </div>
            <div class="iconos">
              <Icon name="ic:baseline-favorite-border"></Icon>
            </div>
          </div>
        </div>        
      </div>
      <div class="abajo">
        <div class="titulos-apartados">
          <p class="titulo-descipcion" @click="setActiveSection('descripcion')"> Descripción</p>
          <p class="titulo-ficha" @click="setActiveSection('informacion')"> Información técnica</p>
        </div>
        <div class="descripcion-apartado" v-if="activeSection === 'descripcion'">
          <p class="descripcion-texto" v-if="article.descripcion">{{ article.descripcion }}</p>
          <div class="descripcion-categorias">
            <h4 class="subtitulo">Categorías</h4>
            <div class="cajasCategorias">
              <p class="categorias">Juego de rol</p>
              <p class="categorias">Juego de rol</p>
              <p class="categorias">Juego de rol</p>
            </div>
          </div>
          <div class="descripcion-reseñas">
            <h4 class="subtitulo">Reseñas</h4>
            <div class="container-reseñas">
              <div class="cajasReseñas">                  
                <div class="estrellas">
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                </div>
                <p class="cabecera-reseña">¡Me encanta este juego!</p>
                <p>Se lo compré a mi novio por su cumpleaños y no lo para de jugar...</p>
              </div>
              <div class="cajasReseñas">
                <div class="estrellas">
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                </div>
                <p class="cabecera-reseña">¡Me encanta este juego!</p>
                <p>Se lo compré a mi novio por su cumpleaños y no lo para de jugar...</p>
              </div>
              <div class="cajasReseñas">
                <div class="estrellas">
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                  <Icon name="material-symbols:star-rate-outline"></Icon>
                </div>
                <p class="cabecera-reseña">¡Me encanta este juego!</p>
                <p>Se lo compré a mi novio por su cumpleaños y no lo para de jugar...</p>
              </div>
            </div>
          </div>
        </div>
        <div class="fichaTecnica-apartado" v-if="activeSection === 'informacion'">
          <div class="columnas">
            <h4 class="subtitulo">Datos</h4>
            <div>
              <p>Un jugador</p>
              <p>Logros en Steam</p>
              <p>Subtítulos disponibles</p>
              <p>HDR disponible</p>
            </div>
          </div>
          <div class="columnas">
            <h4 class="subtitulo">Compatibilidad</h4>
            <div>
              <p>Mandos de XBox</p>
              <p>Mandos DualShock (solo con USB)</p>
              <p>Mandos DualSense (solo con USB)</p>
            </div>
          </div>
          <div class="columnas">
            <h4 class="subtitulo">Idiomas disponibles</h4>
            <div>
              <p>Español (España)</p>
              <p>Inglés</p>
              <p>Francés</p>
              <p>Italiano</p>
              <p>Alemán</p>
              <p>Japonés</p>
              <p>Coreano</p>
              <p>Polaco</p>
              <p>Portugués (Brasil)</p>
              <p>Chino simplificado</p>
              <p>Español (Hispanoamérica)</p>
              <p>Chino tradicional</p>
            </div>
          </div>
          <div class="columnas">
            <h4 class="subtitulo">Requisitos del sistema</h4>
            <div>
              <p>Mínimo:</p>
              <p>Requiere un procesador y un sistema operativo de 64 bits.</p>
              <p>SO: Windows 10 64-bit</p>
              <p>Procesador: 4 core / 8 threads | Intel Core i7-7700 | Ryzen 5 1400</p>
              <p>Memoria: 8 GB de RAM</p>
              <p>Gráficos: 8GB VRAM | GTX 1070 | Radeon RX 580</p>
              <p>DirectX: Versión 12</p>
              <p>Red: Conexión de banda ancha a Internet</p>
              <p>Almacenamiento: 155 GB de espacio disponible</p>
              <p>Notas adicionales: Internet required for non-optional patching, no online play.</p>
            </div>
            <div>
              <p>Recomendado:</p>
              <p>Requiere un procesador y un sistema operativo de 64 bits.</p>
              <p>SO: Windows 10 64-bit</p>
              <p>Procesador: 4 core / 8 threads | Intel Core i5 11600K | Ryzen 5 5600X</p>
              <p>Memoria: 16 GB de RAM</p>
              <p>Gráficos: 8GB VRAM | RTX2070 | RX 6700 XT</p>
              <p>DirectX: Versión 12</p>
              <p>Red: Conexión de banda ancha a Internet</p>
              <p>Almacenamiento: 155 GB de espacio disponible</p>
              <p>Notas adicionales: Internet required for non-optional patching, no online play.</p>
            </div>
          </div>         
        </div>
      </div> 
    </div>
  </div>
</template>
  
<script setup>
  const props = defineProps({
    article: {
      type: Object,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: true
    }
  });
  
  const emit = defineEmits(['close']);
  
  const closeModal = () => {
    emit('close');
  };

  const activeSection = ref('descripcion');

  const setActiveSection = (section) => {
    activeSection.value = section;
  };
</script>
  
<style lang="postcss">
  .modal-overlay {
    position: fixed;
    top: 110px;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: flex-start;
    z-index: 1000;
    max-height: 90vh;
    overflow-y: auto;
  }
  
  .modal-content {
    background: #DEDEDE;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
    max-width: 90%;
    width: 90%;
    border-radius: 40px;
    img{
      height: 480px;
      width: 100%;
      object-fit: cover;
    }
  }
  .medio{
    padding-top: 20px;
  }
  .arriba{
    @apply flex;
    justify-content: space-between;
    padding-bottom: 20px;
    width: 100%;
    align-items: center;
    h2{
      font-size: 35px;
      font-weight: 600;
    }
  }
  .close-button{
    font-size: 45px;
    cursor: pointer; 
    color: #C714E4;
    &:hover{
      background-color: #C714E4;
      color: white;
      border-radius: 50px;
    }
  }
  .caja-precios{
    @apply flex;
    justify-content: space-around;
    align-items: center;
  }
  .precios{
    @apply flex;
    justify-content: space-around;
    align-items: center;
    font-size: 20px;
    font-weight: 400;
    padding-top: 45px;
    padding-bottom: 30px;
  }
  .boton-precios1{
    background-color: #2b2b2b;
    color: white;
    height: auto;
    padding: 10px 70px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;   
    border-radius: 40px; 
    margin-right: 20px;
  }
  .boton-precios2{
    background-color: white;
    color: #2b2b2b;
    height: auto;
    padding: 10px 70px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;   
    border-radius: 40px; 
    border: #2b2b2b solid 3px;
    margin-right: 20px;
  }
  .cantidad{
    color: #C714E4;
    font-weight: 700;
    font-size: 25px;
  }
  .caja-iconos{
    @apply flex;
    justify-content: space-between;
    align-items: center;
    font-size: 45px;
  }
  
  .abajo{
    display: flex;
    flex-direction: column;
    padding: 40px 20px 90px 20px;
    .titulos-apartados{
      @apply flex;
      justify-content: space-around;
      font-size: 20px;
      padding-bottom: 30px;
      border-bottom: #2b2b2b solid 2px;
      &:hover{
        cursor: pointer;
      }
    }
    .descripcion-apartado , .fichaTecnica-apartado{
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      padding-top: 40px;
      text-align: left;
      font-size: 18px;
    }
    
  }

  .descripcion-categorias{
    padding-top: 40px;
    .cajasCategorias{
      @apply flex;
      padding-top: 25px;
      .categorias{
        background-color: #AFAEAE;
        color: white;
        padding: 15px;
        border-radius: 40px;
        margin-right: 25px; 
      }
    }
  }
  
  .subtitulo{
    font-size: 20px;
    font-weight: 600;
    padding-bottom: 15px;
    padding-top: 25px;
  }
  .descripcion-reseñas{
    padding-top: 40px;
    .container-reseñas{
      @apply flex;
      justify-content: space-between;
    }
  }
  .cajasReseñas{
    width: 370px;
    padding: 20px;
    background-color: #AFAEAE;
    border-radius: 40px;
    color: #C714E4;

    .cabecera-reseña{
      font-weight: 700;
    }

    .estrellas{
      font-size: 30px;
    }
    
    .columnas{
    text-align: left;
    margin-top: 40px;
    }
  }
  @media (max-width: 1205px) {
    .medio{
      .precios{
        display: flex;
        flex-direction: column;
        align-items: center;
        .boton-precios1 , .boton-precios2{
          width: 100%;
          margin-bottom: 20px;
        }
      }
      .caja-iconos{
          display: flex;
          flex-direction: column;
          align-items: center;
      }
    }
    .descripcion-reseñas{
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      .container-reseñas{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        .cajasReseñas{
          margin-bottom: 20px;
        } 
      }
    }
    
  }
  
</style>
  