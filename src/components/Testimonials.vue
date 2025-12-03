<template>
  <div class="testimonial-section q-pb-xl q-py-md-xl overflow-hidden">
    <q-img
      class="absolute left-0 top-29"
      :width="$q.screen.gt.sm ? '242px' : '100px'"
      src="src/assets/images/Union.svg"
      alt="left"
    />
    <q-img
      class="absolute right-0"
      :width="$q.screen.gt.sm ? '250px' : '90px'"
      :class="$q.screen.gt.sm ? '':'top-29'"
      src="src/assets/images/Shape.svg"
      alt="right"
    />
    <div class="container q-py-md">
      <div class="row justify-center q-pb-md-xl">
        <div class="col-12 col-md-10 col-xl-12">
            <div class="text-center q-pb-lg">
                <div 
                  class="text-white font-anek font-weight-600"
                  :class="$q.screen.gt.sm ? 'text-h4':'font-size-30'"
                  >Car Lover, Love Us</div>
                <div 
                  class="text-white font-roboto q-pb-md-md"
                  :class="$q.screen.gt.sm ? 'text-h6':'font-siz-18'"
                  >
                    Customer Satisfaction is Our Working Motivation!
                </div>
                </div>
                <Carousel v-bind="carouselConfig">
                <Slide class="flex-column" v-for="(item, i) in testimonialCards" :key="i">
                    <q-card 
                      class="testimonial-card border-radius-30 q-pa-xl"
                      :class="$q.screen.gt.xs ? '':'q-mx-sm'"
                      >
                        <div >
                            <p 
                              class="text-white text-center font-roboto q-mb-lg"
                              :class="$q.screen.gt.md ? 'text-h6':'font-size-18'"
                              >
                                {{ item.text }}
                            </p>
                            <div class="text-center">
                                <q-rating
                                    max="5"
                                    size="27px"
                                    color="white"
                                    v-model="rating"
                                    class="q-mb-md flex justify-center"
                                />
                            </div>
                        </div>
                    </q-card>
                    <div class="q-py-md q-mt-md-md">
                        <div 
                          class="text-center font-roboto text-white font-weight-600"
                          :class="$q.screen.gt.md ? 'font-size-24':'text-h6'"
                          >
                            {{ item.name }}
                        </div>
                        <div class="text-center font-roboto text-white text-h6 text-weight-regular">
                            City Name
                        </div>
                    </div>
                  </Slide>
                  
                  <template #addons>
                    <Pagination :class="$q.screen.gt.sm ? 'q-margin-50':'q-margin-26'" />
                  </template>
            </Carousel>
        </div>
      </div>
    </div>

  </div>
</template>
<script setup>
import { ref } from "vue"
import { Carousel, Slide, Pagination } from "vue3-carousel"
import "vue3-carousel/carousel.css"

const rating = ref(5)

const testimonialCards = [
  {
    text: "My sleep and mood improved after following the recommendations from the test. Blood sugar levels are also reducing with the dietary intervention given.",
    name: "Ibrahim Taimour",
  },
  {
    text: "My sleep and mood improved after following the recommendations from the test. Blood sugar levels are also reducing with the dietary intervention given.",
    name: "Waheed Bin Saeed",
  },
  {
    text: "My sleep and mood improved after following the recommendations from the test. Blood sugar levels are also reducing with the dietary intervention given.",
    name: "Sheikh Yasir",
  }
]

const carouselConfig = {
  itemsToShow: 3,
  wrapAround: true,
  snapAlign: "center",
  autoplay: 5000,
  gap: 40,

  breakpoints: {
    300: {
      itemsToShow: 1,
      snapAlign: "center",
      gap: 10,
    },

    480: {
      itemsToShow: 1,
      snapAlign: "center",
      gap: 15,
    },

    608: {
      itemsToShow: 2,
      snapAlign: "center",
      gap: 20,
    },

    1024: {
      itemsToShow: 3,
      snapAlign: "center",
      gap: 30,
    },

    1280: {
      itemsToShow: 3,
      snapAlign: "center",
      gap: 40,
    },
  },
};

</script>
<style scoped>
.testimonial-section {
    position: relative;
    width: 100%;
    background-color: #071A32;
    background-image: url('/src/assets/images/DeWatermark.ai_1741894540480 1.svg'), radial-gradient(60% 60% at 50% 50%, rgba(48, 24, 28, 0.28) 0%,
            rgba(7, 26, 50, 0.95) 55%,
            #071A32 100%);
    background-size: cover;
    background-position: center;
}

:deep(.carousel__slide) {
    align-items: center;
    display: flex;
    flex-direction: column;
}
.testimonial-card {
  background: linear-gradient(180deg, rgba(12, 12, 12, 0.7) 0%, rgba(30, 53, 81, 0.7) 100%);
  border: 2px solid #F2F2F280;
}
.testimonial-card:hover {
  border: 2px solid #E35F5F;
}
.testimonial-card::after {
  content: "";
  position: absolute;
  left: 50%;
  bottom: -10px;
  width: 16px;
  height: 16px;

  border-left: 2px solid #F2F2F280;
  border-bottom: 2px solid #F2F2F280;

  transform: translateX(-50%) rotate(-45deg);  
}
.q-margin-50{
    margin-bottom: -50px;
}
.q-margin-26{
    margin-bottom: -28px;
}
:deep(.carousel__pagination-button) {
  width: 15px !important;
  height: 15px !important;
  border-radius: 50%;
  background: #ffffff50;
  transition: 0.3s ease;
  border: none;
}

:deep(.carousel__pagination-button--active) {
  background: #ffffff !important;
  width: 16px !important;
  height: 16px !important;
}


</style>