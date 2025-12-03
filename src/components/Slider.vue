<template>
<section class="bg-black q-py-lg">
    <div class="container q-pb-xl">
        <div class="row justify-center q-py-lg">
            <div class="col-12 col-md-10 col-xl-12">
            <div class="row">
                <div class="col-12">
                <div class="text-center">
                    <h4 
                      class="text-white font-weight-600 font-anek "
                      :class="$q.screen.gt.sm ? 'font-size-36':'font-size-28'"
                      >{{ title }} 
                      <span class="text-primary">{{ minititle }}</span></h4>
                    <p class="text-white q-px-sm q-pb-sm font-inter text-weight-regular text-subtitle1">{{ subtitle }}</p>
                </div>
                <div class="row">
                    <div class="col-12">
                        <div class="row">
                            <div class="carousel__wrapper cursor-pointer full-width">

                            <Carousel
                                v-bind="config"
                            >
                                <Slide
                                v-for="(image, index) in images"
                                :key="index"
                                class="q-px-sm"
                                >
                                <q-card
                                    class="no-box-shadow q-pt-md full-width items-center bg-white q-px-lg"
                                    :class="
                                    $q.screen.lt.md
                                        ? 'border-radius-4'
                                        : 'border-radius-4'
                                    "
                                >
                                    <q-img :src="image.url" alt="image" class="images" />
                                    <div class="">
                                    <p class="text-center text-no-wrap text-subtitle1 text-weight-regular text-grey q-pb-none">{{ image.title }}</p>
                                    </div>
                                </q-card>
                                </Slide>

                                <template #addons>
                                <Pagination />
                                </template>
                            </Carousel>

                            </div>
                        </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</section>

</template>
<script setup>
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination } from "vue3-carousel";

defineProps({
  images: Array,
  title: String,
  minititle: String,
  subtitle: String
});

const config = {
  itemsToShow: 1,
  gap: 10,
  snapAlign: "center",
  breakpointMode: "carousel",

  breakpoints: {
    300: { itemsToShow: 1, snapAlign: "start" },
    400: { itemsToShow: 2, snapAlign: "start" },
    500: { itemsToShow: 3, snapAlign: "start" },
    1000: { itemsToShow: 3, snapAlign: "start" },
    1100: { itemsToShow: 6, snapAlign: "start" },
  },
};
</script>
<style scoped>
:deep(.carousel__pagination-button) {
  width: 16px !important;
  height: 16px !important;
  border-radius: 50%;
  background: #FFFFFF !important; 
}

:deep(.carousel__pagination-button--active) {
  background: #EF1D26 !important; 
}

:deep(.carousel__pagination) {
  margin-top: 20px !important;
  margin-bottom: -60px;
}


</style>