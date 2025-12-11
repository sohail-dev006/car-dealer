<template>
  <q-page class="">
    <div class="">
      <HeroCarousel/>
    </div>
    <div class="bg-section">
      <div class="q-py-lg"></div>
      <div class="container">
        <div class="row justify-center">
          <div class="col-12 col-md-10 col-xl-12">
            <div class="row q-col-gutter-md q-px-sm q-px-md-none q-pb-lg">
              <div class="col-12 col-md-8 col-lg-7">
                <q-card class="bg-white border-radius-15 no-shadow q-py-md q-px-sm">
                  <div class="q-px-sm">
                    <h4>Highlights</h4>
                  </div>
                  <div class="row q-px-sm q-col-gutter-sm">
                    <div 
                       v-for="(item, index) in highlights" :key="index" 
                       class="col-6 col-sm-3 col-md-4 col-lg-2">
                      <q-card-actions 
                        class="border-1 bg-grey-13 q-mx-md-sm q-px-lg-none border-radius-5 q-my-sm"
                        :class="$q.screen.gt.md ? 'font-size-18': 'text-subtitle1'" 
                        vertical 
                        align="center"
                      >
                        <q-icon color="primary" size="28px" :name="item.icon" />
                        <div class="text-weight-regular font-kulim text-grey">
                          {{ item.label }}
                        </div>
                        <div class="font-weight-600 font-kulim text-grey-3">
                          {{ item.value }}
                        </div>
                      </q-card-actions>
                    </div>
                  </div>
                </q-card>
                <q-card class="q-my-md bg-white border-radius-15 no-shadow">
                  <q-card-section class="q-pt-sm">
                    <div class="font-size-28 font-weight-600 font-kulim">Description</div>
                    <div class="font-size-18 text-weight-light text-grey-1 font-kulim">
                      2022 Nissan Patrol LE TITANIUM 5.6 with 15″ wheels for sale at Al Futtaim Automall. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam eget pretiums magna. Vivamus eget erat ac lorem interdum malesuada. Mauris a nec mollis mauris, vitae porttitor nunc. 
                    </div>
                  </q-card-section>
                </q-card>
                <q-card class="bg-white q-mb-lg q-pb-lg border-radius-15 no-shadow">
                  <q-card-actions class="q-pl-md">
                    <div class="font-size-28 font-weight-600 font-kulim">Features</div>
                  </q-card-actions>

                  <q-expansion-item
                    v-for="(group, idx) in featureGroups"
                    :key="idx"
                    class="border-expan bg-light-white text-h6 text-grey-4 q-pa-sm font-weight-600 font-kulim"
                    :label="group.title"
                    :model-value="idx === 0"
                  >
                    <div class="row q-col-gutter-x-lg">

                      <div 
                        v-for="(item, i) in group.items"
                        :key="i" 
                        class="col-12 col-sm-6"
                      >
                        <q-item class="bg-white text-weight-regular text-grey text-subtitle1 font-kulim border-expan">
                          <q-item-section class="q-pr-none" top avatar>
                            <q-avatar text-color="primary" :icon="item.icon" />
                          </q-item-section>

                          <q-item-section>
                            <q-item-label>{{ item.label }}</q-item-label>
                          </q-item-section>

                          <q-item-section class="text-center">
                            <q-item-label>{{ item.value }}</q-item-label>
                          </q-item-section>
                        </q-item>
                      </div>

                    </div>
                  </q-expansion-item>
                </q-card>
                <q-card class="q-my-md bg-white border-radius-15 no-shadow">
                  <div class="row">
                    <div class="col-12 col-md-7">
                      <q-card-section class="q-pt-sm">
                        <div class="font-size-28 font-weight-600 font-kulim">
                          {{ description.title }}
                        </div>

                        <div class="font-size-18 text-weight-light text-grey-1 font-kulim">
                          {{ description.shortText }}
                        </div>
                      </q-card-section>

                      <div class="q-pa-md">
                        <q-img :src="description.image" />
                      </div>

                      <div class="font-size-18 q-pa-md text-weight-light text-grey-1 font-kulim">
                        {{ description.longText }}
                      </div>
                    </div>

                    <div class="col-12 col-md-5">
                      <div>

                        <q-item class="font-weight-600 q-pt-md text-h6 font-kulim text-grey">
                          <q-item-section top>
                            {{ description.overall.title }}
                          </q-item-section>

                          <q-item-section side top>
                            <q-item-label>{{ description.overall.rating }}</q-item-label>
                          </q-item-section>
                        </q-item>

                        <div class="q-py-sm" v-for="(item, i) in description.ratings" :key="i">
                          <q-item class="font-weight-600 font-size-15 font-kulim text-grey">
                            <q-item-section avatar class="q-pr-none">
                              <q-icon
                                size="20px"
                                class="text-white border-radius-20"
                                :class="item.bgClass"
                                :name="item.icon"
                              />
                            </q-item-section>

                            <q-item-section class="q-pl-none q-pb-none">
                              {{ item.label }}
                            </q-item-section>

                            <q-item-section side>
                              <q-item-label>{{ item.percent }}%</q-item-label>
                            </q-item-section>
                          </q-item>

                          <div class="q-px-md">
                            <q-linear-progress
                              rounded
                              size="8px"
                              :value="item.percent / 100"
                              :color="item.color"
                            />
                          </div>

                        </div>

                      </div>
                    </div>

                  </div>

                </q-card>
              </div>
              <div class="col-12 col-md-4 col-lg-5">
                <div class="">
                  <q-card class="bg-white border-radius-15 no-shadow">
                    <q-card-section class="">
                      <div  :class="$q.screen.gt.md ?'font-size-26 ':'text-h6'">
                        <div
                           class="font-weight-600 font-mukta">Volvo Xc60 B5 ULTIMATE BRIGHT Suv 2023
                        </div>
                          <q-item class="q-px-none">
                            <q-item-section class="q-px-none font-weight-600 font-mukta text-primary">
                              Price
                            </q-item-section>
                            <q-item-section 
                              class="text-weight-bold font-kulim text-primary q-px-none"
                              :class="$q.screen.gt.md ?'font-size-30 ':'text-h6'"
                              side 
                              top
                              >
                              <q-item-label>AED 137,999</q-item-label>
                          </q-item-section>
                        </q-item>
                      </div>
                      <q-item>
                        <q-item-section 
                          class=" font-mukta font-weight-600 text-grey"
                          :class="$q.screen.gt.md ? 'font-size-24':'text-h6'"
                          >
                          What's included
                        </q-item-section>
                      </q-item>
                      <div class="row q-col-gutter-x-sm q-px-sm-md">
                        <div 
                           v-for="(inc, i) in included"
                           :key="i" 
                           class="col-6 col-sm-4"
                          >
                          <div class="border-1 min-height-132 text-center bg-grey-13 border-radius-5 q-my-sm">
                            <div class="text-center" avatar>
                              <q-avatar class="" size="60px" :icon="inc.icon" />
                            </div>
                            <q-item-section 
                              class="text-weight-regular q-pb-sm text-center font-kulim text-black"
                              :class="$q.screen.gt.md ? 'font-size-16':'font-size-14'"
                            >
                              {{ inc.label }}
                            </q-item-section>
                          </div>
                        </div>
                      </div>
                      <div class="q-px-lg q-py-md">
                        <q-btn
                          v-for="(btn, i) in actionButtons"
                          :key="i"
                          class="full-width q-my-sm border-radius-6 font-poppins"
                          :class="$q.screen.gt.md ? 'text-h6 font-weight-600':'font-size-18 text-weight-medium'"
                          :color="btn.color"
                          :text-color="btn.textColor"
                          :icon="btn.icon"
                          :label="btn.label"
                          @click="btn.action"
                        />
                      </div>
                    </q-card-section>
                  </q-card>
                  <q-card class="bg-car q-ma-sm-lg q-mx-md-none border-radius-15 no-shadow q-my-md">
                    <div class="column items-center q-px-lg relative-position">
                      <q-img
                        src="src/assets/images/Rectangle_color.svg"
                        :width="$q.screen.gt.sm ? ($q.screen.lt.lg ? '240px':'320px') :'280px'"
                      />
                      <div class="absolute-top column items-center q-mt-lg text-white text-center">
                        <div 
                          class="text-weight-bold text-warning q-mb-xs"
                          :class="$q.screen.gt.sm ? ($q.screen.lt.lg ? 'font-size-24':'font-size-28') :'font-size-24'"

                          >
                          ENJOY THE SAFE <br> & SMOOTH DEAL
                        </div>
                        <div 
                          :class="$q.screen.gt.sm ? ($q.screen.lt.lg ? 'font-size-36 line-height-36':'font-size-70 line-height-68') :'font-size-40'"
                          >
                          <div class="text-weight-bold  font-museo">
                            <span>SALE</span>
                          </div>

                          <div class="font-weight-600 text-warning font-kulim">
                            <span>YOUR</span>
                          </div>

                          <div class="text-weight-bold  font-museo">
                            CAR
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="flex q-margin-120 flex-center">
                      <q-img
                        src="src/assets/images/image-car-color.svg"
                        :width="$q.screen.gt.sm ? ($q.screen.lt.lg ? '220px':'400px') :'280px'"
                      />
                    </div>

                    <div class="text-center text-black font-kulim font-weight-600 font-size-28 q-pb-md">
                      No Commission - No Fee
                    </div>

                    <div class="q-px-lg text-center q-pb-lg">
                      <q-btn
                        class="border-radius-10"
                        color="negative"
                        icon="east"
                        label="SALE NOW!"
                      />
                    </div>

                  </q-card>

                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
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
                SIMILAR INVENTORY
              </div>
            </q-item>
            <div class="latest-cars-title relative-position inline-block">
              <div 
               class="text-black font-anek"
              :class="$q.screen.gt.sm ? 'font-size-36 font-weight-600':'text-weight-medium font-size-26'"
               >
               Let's Check Similar <span class="text-primary">
                Cars</span>
              </div>
            </div>
          </div>
          <CarGrid :initialCategories="['hidden']" :initialCars="baseCar" />
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref, reactive } from 'vue';
import Slider from 'src/components/Slider.vue';
import CarGrid from 'src/components/CarGrid.vue';
import HeroCarousel from 'src/components/HeroCarousel.vue';
const title = ref('Browse by');
const title_primary = ref('Brand');
const subtitle = ref('Lorem ipsum dolor sit amet, consectetur.');
const description = ref({
  title: 'Description',
  shortText:
    'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus at erat maximus, egestas nisi sit amet.',
  longText:
    'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus at erat maximus, egestas nisi sit amet.',
  image: 'src/assets/images/image_mac.svg',

  overall: {
    title: 'Overall Rating',
    rating: '7/10'
  },

  ratings: [
    {
      label: 'Exterior Condition',
      percent: 90,
      icon: 'check',
      color: 'purple',
      bgClass: 'bg-pink'
    },
    {
      label: 'Interior Condition',
      percent: 70,
      icon: 'check',
      color: 'pink',
      bgClass: 'bg-yellow'
    },
    {
      label: 'Engine & Transmission',
      percent: 95,
      icon: 'check',
      color: 'purple',
      bgClass: 'bg-pink'
    },
    {
      label: 'Undercarriage & Brakes',
      percent: 55,
      icon: 'check',
      color: 'pink',
      bgClass: 'bg-yellow'
    },
    {
      label: 'Tyres & Rims',
      percent: 80,
      icon: 'check',
      color: 'purple',
      bgClass: 'bg-pink'
    },
  ]
});
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
const carTypes = ['Crossover','Hatchback','Minivan','Sedan','SUV'];
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

const handleBuy = () => {
  console.log("clicked")
}
const handleCar = () => {
  console.log("clicked")
}

const callUs = () => {
  console.log("clicked")
}

const handleWhatsapp = () => {
  console.log("clicked")
}

const handleEmail = () => {
  console.log("clicked")
}

const actionButtons = [
  { label: "Buy Now", textColor: "", color: "primary", action: handleBuy },
  { label: "Compare Car", textColor: "primary", color: "grey-10", action: handleCar },
  { label: "Call Us", textColor: "white", color: "black", action: callUs },
  { label: "Chat ViaWhatsApp", textColor: "",  color: "positive", action: handleWhatsapp },
  { label: "Send E-mail", textColor: "white", color: "black", action: handleEmail },
]
const categories = ['All Cars', ...carTypes]


const highlights = [
  { 
    icon: "place", 
    label: "Location", 
    value: "Dubai" 

  },
  { 
    icon: "event", 
    label: "Model Year", 
    value: "2022" 

  },
  { 
    icon: "route", 
    label: "Kilometers", 
    value: "90,675" 
  },
  { 
    icon: "precision_manufacturing", 
    label: "Engine Cap.", 
    value: "5.6 L" 
  },
  { 
    icon: "settings", 
    label: "Transmission", 
    value: "Automatic" 
  },
  { 
    icon: "verified", 
    label: "Specs", 
    value: "GCC" 
  },
];

const featureGroups = [
  {
    title: "General Condition",
    items: [
      { 
        icon: "calendar_today", 
        label: "Year", 
        value: "2017" 
      },
      { 
        icon: "airline_seat_recline_normal", 
        label: "Seats", 
        value: "Leather Seats" 
      },
      { 
        icon: "speed", 
        label: "Kilometer", 
        value: "97,820 Km" 
      },
      { 
        icon: "build", 
        label: "Transmission", 
        value: "Automatic" 
      },
      { 
        icon: "power", 
        label: "Engine", 
        value: "3 Cylinders" 
      },
      { 
        icon: "local_gas_station", 
        label: "Fuel Type", 
        value: "Petrol" 
      },
      { 
        icon: "event_seat", 
        label: "No. of Seats", 
        value: "7" 
      },
      { 
        icon: "precision_manufacturing", 
        label: "Engine Capacity", 
        value: "3.0 L" 
      },
    ]
  },

  {
    title: "Safety & Convenience",
    items: [
      { 
        icon: "calendar_today", 
        label: "Year", 
        value: "2017" 
      },
      { 
        icon: "airline_seat_recline_normal", 
        label: "Seats", 
        value: "Leather Seats" 
      },
      { 
        icon: "speed", 
        label: "Kilometer", 
        value: "97,820 Km" 
      },
      { 
        icon: "build", 
        label: "Transmission", 
        value: "Automatic" 
      },
      { 
        icon: "power", 
        label: "Engine", 
        value: "3 Cylinders" 
      },
      { 
        icon: "local_gas_station", 
        label: "Fuel Type", 
        value: "Petrol" 
      },
      { 
        icon: "event_seat", 
        label: "No. of Seats", 
        value: "7" 
      },
      { 
        icon: "precision_manufacturing", 
        label: "Engine Capacity", 
        value: "3.0 L" 
      },
    ]
  },

  {
    title: "Interior Condition",
    items: [
      { 
        icon: "calendar_today", 
        label: "Year", 
        value: "2017" 
      },
      { 
        icon: "airline_seat_recline_normal", 
        label: "Seats", 
        value: "Leather Seats" 
      },
      { 
        icon: "speed", 
        label: "Kilometer", 
        value: "97,820 Km" 
      },
      { 
        icon: "build", 
        label: "Transmission", 
        value: "Automatic" 
      },
      { 
        icon: "power", 
        label: "Engine", 
        value: "3 Cylinders" 
      },
      { 
        icon: "local_gas_station", 
        label: "Fuel Type", 
        value: "Petrol" 
      },
      { 
        icon: "event_seat", 
        label: "No. of Seats", 
        value: "7" 
      },
      { 
        icon: "precision_manufacturing", 
        label: "Engine Capacity", 
        value: "3.0 L" 
      },
    ]
  },

  {
    title: "Exterior Condition",
    items: [
      { 
        icon: "calendar_today", 
        label: "Year", 
        value: "2017" 
      },
      { 
        icon: "airline_seat_recline_normal", 
        label: "Seats", 
        value: "Leather Seats" 
      },
      { 
        icon: "speed", 
        label: "Kilometer", 
        value: "97,820 Km" 
      },
      { 
        icon: "build", 
        label: "Transmission", 
        value: "Automatic" 
      },
      { 
        icon: "power", 
        label: "Engine", 
        value: "3 Cylinders" 
      },
      { 
        icon: "local_gas_station", 
        label: "Fuel Type", 
        value: "Petrol" 
      },
      { 
        icon: "event_seat", 
        label: "No. of Seats", 
        value: "7" 
      },
      { 
        icon: "precision_manufacturing", 
        label: "Engine Capacity", 
        value: "3.0 L" 
      },
    ]
  }
];


const included = [
  { 
    icon: "img:/src/assets/images/contract 1.svg", 
    label: "Comprehensive Inspection" 
  },
  { 
    icon: "img:/src/assets/images/contract 1.svg", 
    label: "Extended Warranty" 
  },
  { 
    icon: "img:/src/assets/images/contract 1.svg", 
    label: "Service Contract" 
  },
];
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
.border-1{
  border: 1px solid #DBDBDB !important;
}
.bg-grey-13{
  background-color: #F5F5F5 !important;

}
.bg-section{
  background-color: #F0F0F0;
}
.border-expan{
  border-bottom: 1px solid #8A8A8A;
}
.bg-light-white{
  background-color: #F4F4F4 !important;

}
.bg-car{
  background: linear-gradient(180deg, #1F1F1F 0%, #9E9E9E 100%);

}
.q-margin-120{
  margin-top: -100px;
}
</style>