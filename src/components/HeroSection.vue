<template>
  <div class="q-pa-none">
    <q-carousel
      v-model="slide"
      :height="$q.screen.gt.md ? '850px' : '600px'"
      animated
      infinite
      autoplay
      transition-prev="slide-right"
      transition-next="slide-left"
      control-color="white"
      :arrows="false"
    >
      <q-carousel-slide
        v-for="(item, index) in slides"
        :key="index"
        :name="index"
        class="q-pa-none"
      >
      <div class="dark-overlay"></div>
        <!-- Image -->
        <img
          v-if="item.type === 'image'"
          :src="item.src"
          class="full-slide"
        />

        <!-- Video -->
        <video
          v-else-if="item.type === 'video'"
          :src="item.src"
          autoplay
          loop
          muted
          playsinline
          class="full-slide"
        ></video>

        <!-- Caption -->
         <div class="container">
          <div 
            class="row"
            :class="$q.screen.gt.xl ? 'justify-start':'justify-around'"
            >
            <div class="col-12 col-md-10">
             <div 
               class="slide-caption max-width-540px q-ml-sm-md q-ml-md-sm top-50"
              >
                <h4 class="font-size-26 q-py-xs font-kulim text-primary text-weight-bold">{{ item.subtitle }}</h4>
                <h2 
                  class="font-Marko text-white "
                  :class="$q.screen.gt.sm ? 'line-height-75 font-size-60 text-weight-regular':'text-h4 text-weight-regular'"
                 >
                    <span v-html="highlightDream(item.title)"></span>
                </h2>
                <p class="text-h5 q-pa-sm text-white font-kulim text-weight-regular">{{ item.desc }}</p>
              </div>
            </div>
          </div>
         </div>
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>
<script setup>
import { ref, onMounted } from 'vue'

const slide = ref(0)
const slides = ref([])

onMounted( async () => {

  slides.value = [
    {
      type: "image",
      src: "src/assets/images/background_car.jpg",
      subtitle: "WELCOME TO LOT OF AUTOS",
      title: "Best Way to Find Your Dream Car",
      desc: "Use our search below to find our latest models",
    },
    {
      type: "video",
      src: "https://www.w3schools.com/html/mov_bbb.mp4",
      subtitle: "",
      title: "",
      desc: ""
    },

    {
      type: "image",
      src: "src/assets/images/background_car.jpg",
      subtitle: "WELCOME TO LOT OF AUTOS",
      title: "Best Way to Find Your Dream Car",
      desc: "Use our search below to find our latest models",
    }
  ]
})
const highlightDream = (text) => {
  return text.replace(/Dream/g, '<span class="text-primary">Dream</span>')
}

</script>
<style scoped>

.full-slide {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  max-width: 100%;
  overflow: hidden;
  z-index: 0;
}
.q-carousel-slide {
  overflow: hidden !important;
}
.slide-caption {
  position: absolute;             
  transform: translateY(-50%);
  z-index: 2;
}

.dark-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #000000A6; 
  z-index: 1;
}
@media (max-width: 768px) {
  .slide-caption {
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    width: 80%;
  }
}
@media (min-width: 1919px) and (max-width: 2500px) {
  .slide-caption {
    left: 14%;

  }
}
</style>

