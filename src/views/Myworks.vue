<script setup>
import MyModal from '@/components/MyModal.vue';
import { ref } from 'vue';
import imageCV from '@/assets/image-CV.jpg';
import cv from '@/assets/cv.jpeg';
import cv1 from '@/assets/cv1.jpg';
import form from '@/assets/form.png';
import form2 from '@/assets/form2.jpg';
import photo from '@/assets/photo.jpg';
import cahierdescharges from '@/assets/cahierdescharges.jpg';
import cahierdescharges1 from '@/assets/cahierdescharges1.jpg';
import formulaire from '@/assets/formulaire.jpg';
import maquette from '@/assets/maquette.jpg';
import maquetteintegration from '@/assets/maquetteintegration.jpg';

const creations = ref([
  {
    title: "Curriculum Vitae",
    image: imageCV,
    modalImage: cv,
    modalImage2: cv1,
    details: [
      { label: "Date de création", value: "novembre 2023" },
      { label: "Technologies utilisées", value: "HTML5, CSS3" },
    ],
    github: "https://github.com/Mahadali-miryam/CV-1" 
  },
{
    title: "Cahier des charges",
    image: cahierdescharges,
    modalImage:cahierdescharges ,
    modalImage2:cahierdescharges1,
    details: [
      { label: "Date de création", value: "Décembre 2023" },
      { label: "Technologies utilisées", value: "word" },
    ],
    pdf: "https://1drv.ms/b/s!AuY0AhENKkSS3gSSgi21soB2bVNM?e=BVgATT"
    
  },
  
  {
    title: "Formulaire",
    image: formulaire,
    modalImage:form,
    modalImage2:form2,
    
    details: [ 
      { label: "Date de création", value: "Janvier 2024" },
      { label: "Technologies utilisées", value: "HTML5, CSS, et Java-Script" },
    ],
    github: "https://github.com/Mahadali-miryam/devoir-dynamiser-un-espace-commentaire" 
  },

  {
    title: "Maquette MY HOMESPACE",
    image: maquette,
    modalImage:maquetteintegration,
    modalImage2:photo,
    details: [
    { label: "Date de création", value: "Janvier 2024" },
      { label: "Technologies utilisées", value: "HTML5, CSS" },
    ],
    github: "https://github.com/Mahadali-miryam/exercice-My-Home-Space" 
  },
]);
const modalOpen = ref(false);
   const selectedCreation = ref({});

   function openModal(creation) {
     selectedCreation.value = creation;
     modalOpen.value = true;
   }

   function closeModal() {
     modalOpen.value = false;
   }
</script>
<template>
  <main>
  <div id="realisations" class="creations-container">
    <h1 class="creations-title">Mes créations</h1> 
  <!-- Boucle à travers les créations et affiche chaque création -->
  <div v-for="(creation, index) in creations" :key="index" class="creation">
    <img :src="creation.image" :alt="creation.title" @click="openModal(creation)" class="creation-image" >
      <p>{{ creation.title }}</p>
  </div>
  </div>
  <!-- Inclut la modale et passe les props nécessaires  -->
  <MyModal :creation="selectedCreation" :modalOpen="modalOpen" @closeModal="closeModal" />
</main> 
</template>

<style scoped>
.creations-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center; 
  background-color: #f2f2f2;
  padding-bottom: 70px;
}

.creation {
  transition: transform 0.3s ease;
  text-align: center;
  width: 40%;
  margin-bottom: 25px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1); 
}

.creation:hover {
  transform: translateY(-5px);
  box-shadow: 10px 10px 15px rgba(255, 215, 0, 0.4);
}

.creation-image {
  width: 40%; 
  border-radius: 8px;
  margin-bottom: 5px;
 
}

.creation p {
  text-align: center;
  color: #333;
}

.creations-title  {
  color: #333;
  text-transform: uppercase;
  font-size: 2rem;
  text-align: center;
  width: 100%;
  margin-bottom: 1.5rem;
  font-family: "Poppins", sans-serif;
  font-weight: 600;
}

/* Responsive design */
@media (max-width: 768px) {
  .creations-container {
    padding-bottom: 30%; 
    padding-top: 15%;
  }

  .creation {
    width: calc(50% - 20px); /* Deux créations par ligne sur les appareils mobiles */
    margin-bottom: 50px;
  }

  .creation-image {
    width: 80%;  
    margin-bottom: 10px; 
    margin-left: auto; 
    margin-right: auto
  }

  .creations-title {
    font-size: 1.8rem;
    margin-bottom: 2rem; 
  }
}
</style>