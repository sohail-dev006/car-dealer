<template>
  <q-page class="">

    <div class="">
      <Slider :images="sliderImages" :title="title" :minititle="title_primary" :subtitle="subtitle"/>
    </div>

    <div class="container">
      <div class="row justify-center q-py-md q-py-md-lg">
        <div class="col-12 col-md-10 col-xl-12">
          <div class="text-center">
            <q-item class="q-pl-none text-center justify-center items-center">
              <q-icon size="28px" name="img:/src/assets/images/car_icon.svg" />
              <div class="font-anek q-pt-xs q-pl-sm text-primary font-size-20 text-weight-medium">
                NEW ARRIVALS
              </div>
            </q-item>
            <div class="latest-cars-title relative-position inline-block">
              <div 
               class="text-black font-anek"
              :class="$q.screen.gt.sm ? 'font-size-36 font-weight-600':'text-weight-medium font-size-26'"
               >
               Let's Check Latest <span class="text-primary">
                Cars</span>
              </div>
            </div>
          </div>
          <CarGrid :initialCategories="['hidden']" :initialCars="cars" />
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref, reactive } from 'vue';
import DynamicForm from 'src/components/DynamicForm.vue';
import HeroSection from 'src/components/HeroSection.vue';
import Slider from 'src/components/Slider.vue';
import CarGrid from 'src/components/CarGrid.vue';
import Testimonials from 'src/components/Testimonials.vue';
import HeroCarousel from 'src/components/HeroCarousel.vue';
const title = ref('Browse by');
const title_primary = ref('Brand');
const subtitle = ref('Lorem ipsum dolor sit amet, consectetur.');
const formModel = ref({
  carCondition: 'All Status',
  brand: 'All Brand',
  carModel: 'All Model',
  priceRange: 'Price Range',
  year: 'All Year',
  mileage: 'All Mileage',
  bodyType: 'All Body Type'
});

const fields = ref([
  {
    label: "Car Condition",
    model: "carCondition",
    fieldType: "select",
    options: [
      { label: 'All Status', value: 'All Status' },
      { label: 'New', value: 'New' },
      { label: 'Used', value: 'Used' },
      { label: 'Reconditioned', value: 'Reconditioned' }
    ],
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  },
  {
    label: "Brand Name",
    model: "brand",
    fieldType: "select",
    options: [
      { label: 'All Brand', value: 'All Brand' },
      { label: 'Toyota', value: 'Toyota' },
      { label: 'Honda', value: 'Honda' },
      { label: 'Suzuki', value: 'Suzuki' }
    ],
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  },
  {
    label: "Car Model",
    model: "carModel",
    fieldType: "select",
    options: [
      { label: 'All Model', value: 'All Model' },
      { label: 'Corolla', value: 'Corolla' },
      { label: 'Civic', value: 'Civic' },
      { label: 'Swift', value: 'Swift' }
    ],
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  },
  {
    label: "Price Range",
    model: "priceRange",
    fieldType: "select",
    options: [
      { label: 'Price Range', value: 'Price Range' },
      { label: '10-20 Lac', value: '10-20' },
      { label: '20-30 Lac', value: '20-30' },
      { label: '30-50 Lac', value: '30-50' }
    ],
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  },
  {
    label: "Choose Year",
    model: "year",
    fieldType: "select",
    options: [
      { label: 'All Year', value: 'All Year' },
      { label: '2024', value: '2024' },
      { label: '2023', value: '2023' },
      { label: '2022', value: '2022' }
    ],
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  },
  {
    label: "Choose Mileage",
    model: "mileage",
    fieldType: "select",
    options: [
      { label: 'All Mileage', value: 'All Mileage' },
      { label: '0 - 30k', value: '0-30k' },
      { label: '30k - 60k', value: '30k-60k' },
      { label: '60k+', value: '60k+' }
    ],
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  },
  {
    label: "Body Type",
    model: "bodyType",
    fieldType: "select",
    options: [
      { label: 'All Body Type', value: 'All Body Type' },
      { label: 'Sedan', value: 'Sedan' },
      { label: 'SUV', value: 'SUV' },
      { label: 'Hatchback', value: 'Hatchback' }
    ],
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  },
  {
    fieldType: "button",
    btnlabel: "Find Your Car",
    icon: "search",
    colClass: "col-12 col-sm-6 col-md-3 q-px-sm",
  }
]);

const aboutUsSection = reactive({
  image: 'src/assets/images/car_pic.jpg',
  icon: 'img:/src/assets/images/car_icon.svg',
  label: 'ABOUT US',
  title: 'Middle East Largest',
  highlighted: 'Car Dealer',
  subtitle: 'Marketplace.',
  description: 'It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters.',
  features: [
    'Vivamus suscipit est eleifend erat laoreet luctus.',
    'Curabitur vehicula sapien a mauris feugiat.',
    'Donec posuere lorem at sapien commodo.',
    'Pellentesque habitant morbi tristique senectus.'
  ],
  buttonLabel: 'Discover More'
})

const onClick = () => {
  console.log('Button clicked!')
}
const sliderImages = ref([
  { 
    url: "src/assets/images/BMW.svg",
    title: "BMW ",
  },
  { 
    url: "src/assets/images/Nissan.svg",
    title: "Nissan"
  },
  { 
    url: "src/assets/images/RollsRoyce.svg",
    title: "Show All Brands"
  },
  { 
    url: "src/assets/images/Tesla.svg", 
    title: "Tesla"
  },
  { 
    url: "src/assets/images/BMW.svg",
    title: "BMW"
  },
  { 
    url: "src/assets/images/Ferrari.svg",
    title: "Show All Brands"
  },
  { 
    url: "src/assets/images/Mercedes.svg", 
    title: "Mercedes-Benz"
  },
]);
const carTypes = ['Crossover','Hatchback','Minivan','Sedan','SUV']
const baseCar = [
      { 
        type: 'Crossover',
        name:'Dongfeng Aeolus Yixuan Mach', 
        model:2023,
        year: '2025',
        btColor: 'bg-white text-primary',
        badgeColor: 'bg-primary text-white', 
        transmission:'Auto', 
        fuel:'Petrol', 
        seats:'2 Seats',
        km: '10,000', 
        power:'Power', 
        image:'src/assets/images/image_1.svg',
        price: '12000',
        pic: '7', 
      },
      { 
        type: 'Hatchback',
        name:'Dongfeng Aeolus Yixuan Mach',
        model:2023,
        year: '2025',
        btColor: 'bg-white text-primary',
        badgeColor: 'bg-primary text-white', 
        transmission:'Auto', 
        fuel:'Petrol', 
        seats:'2 Seats',
        km: '10,000', 
        power:'Power', 
        image:'src/assets/images/image_3.svg', 
        price: '12000',
        pic: '7',
      },
      { 
        type: 'Sedan',
        name:'Dongfeng Aeolus Yixuan Mach',
        model:2023,
        year: '2025',
        btColor: 'bg-white text-primary',
        badgeColor: 'bg-primary text-white', 
        transmission:'Auto', 
        fuel:'Petrol', 
        seats:'2 Seats',
        km: '10,000', 
        power:'Power', 
        image:'src/assets/images/image_1.svg', 
        price: '12000',
        pic: '7',
      },
      { 
        type: 'Minivan',
        name:'Dongfeng Aeolus Yixuan Mach',
        model:2023,
        year: '2025',
        btColor: 'bg-white text-primary',
        badgeColor: 'bg-primary text-white', 
        transmission:'Auto', 
        fuel:'Petrol', 
        seats:'2 Seats',
        km: '10,000', 
        power:'Power', 
        image:'src/assets/images/image_2.svg', 
        price: '12000',
        pic: '7',
      },
];
const cards = [
  {
    title: "Best Services",
    desc: "Our staff consists of dedicated and certified A+ and Network",
    img: "src/assets/images/image_car.svg"
  },
  {
    title: "Best Staf",
    desc: "Our staff consists of dedicated and certified A+ and Network",
    img: "src/assets/images/image_car.svg"
  },
  {
    title: "Simple Pricing",
    desc: "Our staff consists of dedicated and certified A+ and Network",
    img: "src/assets/images/image_car.svg"
  },
  {
    title: "Warranty",
    desc: "Our staff consists of dedicated and certified A+ and Network",
    img: "src/assets/images/image_car.svg"
  }
];
const cars = baseCar;

const categories = ['All Cars', ...carTypes]


</script>
<style scoped>
.my-card {
  margin-top: -83px;
  z-index: 6;
}
:deep(.q-item__section--avatar) {
    color: inherit;
    min-width: 36px;
}

.latest-cars-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  height: 5px; 
  width: 100%;
  background: linear-gradient(
    to right,
    white 35%,        
    #EF1D26 5%,       
    #ffffff 50%,       
    #EF1D26 70%,       
    white 55%
    
  );
  border-radius: 5px;
}
.bottom-rounded {
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  border-bottom: 5px solid #EF1D26;
  overflow: hidden; 
}


</style>