<template>
     <div class="scroll-container">
    <div class="scroll-content">
      <img src="" alt="Image 1" />
      <img src="image2.jpg" alt="Image 2" />efref
      <img src="image3.jpg" alt="Image 3" />
      <img src="image4.jpg" alt="Image 4" />
      <!-- Ajoutez autant d'images que nécessaire -->
    </div>
    </div>
</template>






<style scoped>
.scroll-container {
    width: 100%; /* Largeur du conteneur visible */
    height: 200px; /* Hauteur souhaitée du conteneur */
    overflow: hidden; /* Cache les éléments débordants */
    position: absolute;
    color: bisque;
  }

  .scroll-content {
    display: flex;
    flex-direction: row;
    animation: scroll-horizontal 10s linear infinite; /* Durée et répétition */
  }

  .scroll-content img {
    width: 200px; /* Largeur des images */
    height: auto;
    margin-right: 10px; /* Espacement entre les images */
  }

  @keyframes scroll-horizontal {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(-100%);
    }
  }

</style>
