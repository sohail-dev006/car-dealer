<template>
  <q-layout view="lHh Lpr lFf">
    <div class="top-bar gt-sm relative-position">
      <div 
        class="left-red bg-primary"
        :class="$q.screen.lt.lg ? 'width-90px':'width-150px'"
      >
      </div>

      <div class="center-black absolute-full">
        <div class="content">
          <div class="container">
            <div class="row justify-center">
              <div class="col-md-10 col-lg-10 col-xl-12">
                <q-toolbar>
                  <div class="col-6 col-lg-6">
                    <div class="">
                      <template v-for="(contact, index) in contacts.left" :key="index">
                        <q-icon :name="contact.icon" class="q-mr-sm q-pb-xs" size="25px" />
                        <a
                          class="text-decoration font-anek content text-white font-14 text-weight-medium q-pr-lg q-pt-sm"
                          :href="contact.link"
                        >{{ contact.text }}</a>
                      </template>
                    </div>
                  </div>
  
                  <q-space />
  
                  <div class="col-6 col-lg-6 text-right content">
                    <template v-for="(contact, index) in contacts.right" :key="index">
                      <q-icon :name="contact.icon" class="q-pl-lg q-pb-xs q-mr-sm" size="25px" />
                      <a
                        class="text-decoration font-anek text-white font-14 text-weight-medium"
                        :href="contact.link"
                      >{{ contact.text }}</a>
                    </template>
                  </div>
                </q-toolbar>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div 
        class="right-red bg-primary"
        :class="$q.screen.lt.lg ? 'width-90px':'width-150px'"
      ></div>
    </div>

    <div class="bg-white shadow-1">
      <div class="container q-py-sm">
        <div 
          class=""
          :class="$q.screen.gt.sm ? 'row justify-center':''"
          >
          <div class="col-12 col-sm-10 col-xl-12">
            <q-toolbar class="q-pl-none justify-between">
              <div class="col-6 col-md-auto col-lg-2">
                <q-item class="q-px-none">
                  <q-item-section class="q-px-none" top avatar>
                    <q-img width="65px" src="/src/assets/images/logo.jpg" />
                  </q-item-section>
                  <q-item-section>
                    <q-item-label class="">
                      <q-img 
                        src="src/assets/images/LOTOFAUTOS.png" 
                        :width="$q.screen.gt.md ? 'q-pt-xs' : '100px'"
                        />
                    </q-item-label>
                    <q-item-label 
                      class="text-black" 
                      caption 
                      :class="$q.screen.gt.md ? 'font-size-18 text-weight-regular':''"
                      lines="1">
                      WE SELL QUALITY
                    </q-item-label>
                  </q-item-section>
                </q-item>
              </div>

              <div class="col-sm-10 gt-sm">
                <div class="row q-mr-lg-none items-center justify-end q-gutter-sm no-wrap nav-row">
                  <router-link
                    v-for="(link, index) in navLinks"
                    :key="index"
                    class="nav-link text-decoration font-anek text-black text-weight-medium"
                    :class="$q.screen.gt.md ? 'font-size-18 q-px-sm':'font-size-14 q-px-lg-sm'"
                    :to="link.path"
                  >
                    {{ link.label }}
                  </router-link>

                  <q-btn
                    label="GET HELP"
                    icon-right="arrow_right_alt"
                    class="q-ml-md border-radius-10 bg-primary text-white"
                  />
                </div>
              </div>
              <div class="col-6 col-sm-shrink lt-md text-right">
                <q-btn
                  dense
                  flat
                  round
                  :icon="drawer ? 'close':'menu'"
                  @click="drawer = !drawer"

                />
                

              </div>
            </q-toolbar>
          </div>
        </div>

        <transition class="lt-md" name="slide">
          <div 
            v-if="drawer" 
            class="mobile-menu shadow-2"
          >
            <div class="column text-left q-py-md q-px-lg">
              <router-link
                v-for="(link, index) in navLinks"
                :key="index"
                class="mobile-nav-link text-decoration font-anek text-black text-weight-medium q-my-sm"
                :to="link.path"
                @click="drawer = false"
              >
                {{ link.label }}
              </router-link>
              <div class="">
                <q-btn
                    label="GET HELP"
                    icon-right="arrow_right_alt"
                    class="q-mt-sm border-radius-10 bg-primary text-white"
                  />
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>

    <q-page-container>
      <router-view />
    </q-page-container>
    
  <footer class="bg-dark q-pt-xl q-pb-lg">
    <div class="container">
      <div class="row justify-center q-px-sm q-px-md-none">
        <div class="col-12 col-md-10 col-xl-12">
          <div class="row q-col-gutter-xl q-gutter-y-xl">
            <div class="col-12 col-sm-6 col-md-5 col-lg-4">
              <q-toolbar class="text-white q-pl-none">
                  <q-img 
                      src="/src/assets/images/logo.jpg" 
                      width="62px"
                    />                      
                <q-toolbar-title>
                  <div>
                    <q-img 
                      src="src/assets/images/LOTOFAUTOS.svg" 
                      :width="$q.screen.gt.sm ? '132px' : '100px'"
                      />
                  </div>
                  <div
                    class="text-grey-2"  
                    :class="$q.screen.gt.md ? 'font-size-18 text-weight-regular':'text-subtitle2'"
                    >
                    WE SELL QUALITY
                  </div>
                </q-toolbar-title>
              </q-toolbar>

              <div class="text-white font-roboto q-py-sm text-subtitle1 text-weight-regular">
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque luctus luctus dolor, egestas fringilla massa vehicula non. Praesent dignissim erat quis.</p>
              </div>

              <div class="q-mt-md ">
                <q-item v-for="(item,i) in contactItems" :key="i" class="q-pl-none q-py-xs">
                  <q-item-section avatar>
                    <q-icon :name="item.icon" class="bg-primary text-white q-pa-sm border-radius-10" />
                  </q-item-section>
                  <q-item-section class="q-py-sm-md font-roboto text-weight-regular text-h6 text-white">
                    {{ item.text }}
                  </q-item-section>
                </q-item>
              </div>
            </div>
            <div class="col-6 col-sm-6 col-md-2 col-lg-2">
              <div class="border-bottom q-pb-md relative-position inline-block">
                <h6 
                  class="text-white  font-anek font-weight-600 font-anek"
                  :class="$q.screen.gt.md ? 'font-size-22':'text-h6'"
                  >Car Partner</h6>
              </div>

              <q-item v-for="(item,i) in carPartner" :key="i"
                      class="q-pl-none q-py-none items-center">
                <q-icon name="img:/src/assets/images/expand_circle_right.svg" class="text-white" size="24px" />
                <q-item-section class="text-weight-light q-py-none font-size-18 text-white q-pl-sm font-mukta">
                  {{ item }}
                </q-item-section>
              </q-item>
            </div>
            <div class="col-6 col-sm-6 col-md-2 col-lg-3">
              <div class="border-bottom q-pb-md relative-position inline-block">
                <h6 
                   class="text-white font-anek font-weight-600 font-anek"
                  :class="$q.screen.gt.md ? 'font-size-22':'text-h6'"
                   >Useful Links</h6>
              </div>

              <q-item v-for="(item,i) in usefulLinks" :key="i"
                      class="q-pl-none q-py-none items-center">
                <q-icon name="img:/src/assets/images/expand_circle_right.svg" class="text-grey-5" size="24px" />
                <q-item-section class="text-weight-light q-py-none font-size-18 text-white q-pl-sm font-mukta">
                  {{ item }}
                </q-item-section>
              </q-item>
            </div>
            <div class="col-12 col-sm-6 col-md-3 col-lg-3">
              <div class="border-bottom q-pb-md relative-position inline-block">
                <h6 
                  class="text-white font-anek font-weight-600 font-anek"
                  :class="$q.screen.gt.md ? 'font-size-22':'text-h6'"
                  >Newsletter</h6>
                </div>

              <div class="text-subtitle1 font-roboto q-py-md text-weight-regular text-white">
                Subscribe Our Newsletter To Get Latest Update And News
              </div>

              <div 
                class="text-subtitle1 font-roboto q-py-sm text-weight-regular text-white"
                >Enter your email id</div>

              <q-input 
                dense 
                outlined 
                v-model="email" 
                placeholder="Your Email"
                class="bg-white text-grey border-radius-10" 
              />

              <q-btn
                no-caps
                class="full-width q-mt-md border-radius-10 bg-primary text-white"
                icon-right="arrow_right_alt"
                label="Subscribe Now"
              />
            </div>
          </div>
      </div>
    </div>

    </div>
    <div class="footer-bar q-mt-lg q-py-md">
      <div class="row justify-center z-in full-width q-px-sm q-px-md-none"
      
      >
        <div 
          class="col-12 col-md-10 col-lg-9 max-width-1440 q-px-xl-md"
          >
          <div class="row">
            <div class="col-12 col-sm-6 text-start">
              <div 
                class="text-white font-size-16 font-kulim text-weight-regular"
                :class="$q.screen.gt.sm ? '':'text-center q-py-xs'">
                © Copyright 2025 LOT <span class="text-primary">OF</span> AUTOS. All Rights Reserved.
              </div>
            </div>
            <div class="col-12 col-sm-6 text-right">
              <div 
                class="row items-center q-gutter-sm"
                :class="$q.screen.gt.sm ? 'justify-end':'justify-center q-py-xs'"
                >
                <q-btn 
                  dense
                  icon="facebook"
                  flat
                  class="bg-white text-primary border-radius-10"
                   />
                <q-btn 
                  dense
                  icon="img:/src/assets/images/twitter-boxed-svgrepo-com.svg" 
                  flat 
                  class="bg-white text-primary border-radius-10" 
                />
                <q-btn 
                  dense
                  icon="img:/src/assets/images/linkedin-in-svgrepo-com.svg"
                  flat
                  class="bg-white text-primary border-radius-10"
                   />
                <q-btn 
                  dense
                  icon="img:/src/assets/images/youtube-color-svgrepo-com.svg" 
                  flat 
                  class="bg-white text-primary border-radius-10" 
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </footer>
  </q-layout>
</template>

<script setup>
import { reactive, onMounted, ref } from 'vue'
import { useQuasar } from 'quasar'
let drawer = ref(false)

const $q = useQuasar()


const contacts = reactive({
  left: [
    { icon: 'img:/src/assets/images/alarm-svgrepo-com.svg',
      text: 'info@lotofautos.com',
      link: 'mailto:info@lotofautos.com' 
    },
    { icon: 'img:/src/assets/images/Group.svg',
      text: 'support@lotofautos.com',
      link: 'mailto:support@lotofautos.com' 
    }
  ],
  right: [
    { icon: 'img:/src/assets/images/whatsapp-svgrepo-com .svg',
      text: '(201) 428-1034',
      link: 'https://wa.me/12014281034' 
    },
    { icon: 'img:/src/assets/images/Call.svg',
      text: '(201) 428-1034',
      link: 'tel:+12014281034' 
    }
  ]
})


const navLinks = reactive([
  { label: 'HOME',
    path: '/' 
     
  },
  { label: 'BUY A CAR',
    path: '/buy' 
     
  },
  { label: 'SELL / TRADE',
    path: '/sell' 
     
  },
  { label: 'OFFERS',
    path: '/offers' 
     
  },
  { label: 'FINANCE',
    path: '/finance' 
     
  },
  { label: 'SERVICE',
    path: '/service' 
     
  },
  { label: 'ABOUT US',
    path: '/about' 
     
  },
  { label: 'CONTACT US',
    path: '/contact' 
     
  }
])

const email = ref("")

const contactItems = [
  { 
     icon: "call", 
     text: "+97 123 654 7898" 
  },
  { 
     icon: "email", 
     text: "support@lotofautos.com" 
  },
  { 
     icon: "location_on", 
     text: "25/B Milford Road, New York" 
  }
]

const carPartner = [
  "Audi", "BMW", "Mercedes Benz", "Lamborghini",
  "Rolls Royce", "Bentley", "Toyota"
]

const usefulLinks = [
  "Home", "Used Cars", "New Cars", "About Us",
  "FAQs", "Contact Us", "Privacy Policy"
]

</script>

<style scoped>
.top-bar {
  height: 50px;
  width: 100%;
  display: flex;
  overflow: hidden;
}

.left-red {
  clip-path: polygon(0 0, 63% 0, 100% 100%, 0 100%);
  display: flex;
  z-index: 2;
  align-items: end;
}

.center-black {
  background: #000;
  flex: 1;
  z-index: 0;
  clip-path: polygon(0 0, 96% 0, 100% 100%, 0 100%);
}

.right-red {
  position: absolute;
  top: 0;
  right: 0;
  height: 50px;
  clip-path: polygon(37% 0, 100% 0, 100% 100%, 0 100%);
  display: flex;
  align-items: center;
  justify-content: flex-end;
  z-index: 3;
}
.red-footer{
  position: absolute;
  top: 0;
  right: 0;
  height: 50px;
  clip-path: polygon(37% 0, 100% 0, 100% 100%, 0 100%);
  display: flex;
  align-items: center;
  justify-content: flex-end;
  z-index: 3;
}

.content{
  position: relative !important;
  z-index: 10 !important;
}
.nav-link:hover {
  color: #e10600 !important;
}
.nav-row{
  gap: 8px;
}

@media (min-width: 1024px) and (max-width: 1200px) {

  .nav-row {
    gap: 8px !important;  
  }

  .nav-row .q-btn {
    padding: 0 10px !important; 
    font-size: 13px !important;
    flex-shrink: 0;
    white-space: nowrap;
  }
}


.nav-row {
  flex-wrap: nowrap;
}

.nav-row .nav-link {
  white-space: nowrap;
  flex-shrink: 1;
}

.nav-row .q-btn {
  white-space: nowrap;
  flex-shrink: 0;
  padding: 6 12px;
}

.slide-enter-from,
.slide-leave-to {
  max-height: 0;
  opacity: 0;
}

.slide-enter-to,
.slide-leave-from {
  max-height: 400px;
  opacity: 1;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.35s ease;
}
.bg-dark-1{
  background-color:#1F1F1F;
  /* background-color: #e10600; */
  z-index: 0;
}

.border-bottom::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  top: 33px;
  height: 5px; 
  width: 100%;
  background: linear-gradient(
    to right,
    #565656 15%,        
    #EF1D26 40%,       
    #565656 0%,       
    #EF1D26 20%,       
    #565656 0%
    
  );
  border-radius: 5px;
}

.footer-bar {
  position: relative;
  /* height: 60px; */
  display: flex;
  align-items: center;
  overflow: hidden;
  background: #353535 !important;
}

.footer-bar::before {
  position: absolute;
  inset: 0;
  background: #353535 !important;
  z-index: 1;
}

.footer-bar::after {
  content: "";
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  width: 50%; 
  background: #e10600;
  z-index: 2;
  clip-path: polygon(10% 0, 100% 0, 100% 100%, 0 100%);
}

.footer-content {
  position: relative;
  z-index: 3;
}
.z-in{
  z-index: 6;
}

</style>
