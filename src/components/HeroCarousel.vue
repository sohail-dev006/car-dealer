<template>
  <div class="car-full-wrapper">
    <q-carousel
      v-model="slide"
      swipeable
      animated
      infinite
      arrows
      transition-prev="slide-right"
      transition-next="slide-left"
      class="bg-black full-width"
    >
      <q-carousel-slide
        v-for="(img, index) in images"
        :key="index"
        :name="index"
        class="flex flex-center"
      >
        <div class="car-flex row no-wrap justify-center items-center">

          <q-img
            :src="prevImage(index)"
            class="side-img fade"
            fit="cover"
          />

          <q-img
            :src="img"
            class="center-img"
            fit="contain"
          />

          <q-img
            :src="nextImage(index)"
            class="side-img fade"
            fit="cover"
          />

        </div>
      </q-carousel-slide>
    </q-carousel>

  </div>
</template>
<script setup>
import { ref } from "vue";

const slide = ref(0);

const images = ref([
  "src/assets/images/Frame 1000002066.svg",
  "src/assets/images/Frame 1000002066.svg",
  "src/assets/images/Frame 1000002066.svg",
  "src/assets/images/Frame 1000002066.svg",
]);

const prevImage = (i) => {
  const p = i - 1 < 0 ? images.value.length - 1 : i - 1;
  return images.value[p];
};

const nextImage = (i) => {
  const n = i + 1 >= images.value.length ? 0 : i + 1;
  return images.value[n];
};
</script>
<style scoped>
.car-full-wrapper {
  width: 100%;
  overflow: hidden;
}

.car-flex {
  width: 100%;
  height: 100%;
  display: flex;
  gap: 0 !important;
  padding: 0;
  margin: 0;
}
:deep(.center-img .q-img__image),
:deep(.side-img .q-img__image) {
  height: 100% !important;
  width: 100% !important;
  object-fit: cover !important;
}
.car-flex {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.center-img {
  width: 55%;    
  height: 100%;
  object-fit: contain;
}

.side-img {
  width: 28%;  
  height: 100%;
  opacity: 0.6;
  object-fit: cover;
}

@media (max-width: 1024px) {
  .side-img {
    display: none;
  }
  .center-img {
    width: 100%;
  }
}

:deep(.q-carousel__control) {
  background: white !important;
  color: #EF1D26 !important;
  width: 48px;
  height: 48px;
  border-radius: 5px;
  top: 50% !important;                 
  transform: translateY(-50%) !important;
}
:deep(.q-carousel__slide, .q-carousel .q-carousel--padding){
  padding: 0px !important;
}

</style>
