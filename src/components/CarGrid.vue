<template>
    <div class="q-py-xl q-mx-auto">

        <!-- FILTERS -->
        <div v-if="initialCategories != 'hidden'" class="row items-center justify-between q-mb-sm q-px-sm">
            <div class="col-sm-auto q-mb-sm q-mb-sm-none">
              <div class="category-tabs flex">
                <div
                    v-for="cat in categories"
                    :key="cat"
                    class="cat-btn-wrapper text-center"
                    @click="activeCategory = cat"
                >
                    <q-btn
                        flat
                        no-caps
                        :label="cat"
                        class="cat-btn font-size-20 font-kulim"
                        :color="activeCategory === cat ? 'primary' : 'grey-7'"
                    />


                    <div
                    v-if="activeCategory === cat"
                    class="cat-underline bg-primary"
                    ></div>
                </div>
                </div>
            </div>
            
            <div class="col-auto">
                <q-select dense outlined v-model="sortBy" :options="sortOptions" style="width: 180px" />
            </div>
        </div>
        <q-separator class="q-mb-md" inset />

        <!-- CAR GRID -->
        <div class="row q-col-gutter-lg">
            <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="car in filteredCars" :key="car.id">
                <q-card class="q-pa-sm bg-white border-radius-20" style="border: 1px #DEDEDE;">
                    <div class="relative-position">

                        <q-badge 
                            :color="car.badgeColor" 
                            rounded
                            class="absolute-top-left q-ma-md z-index font-size-14 text-weight-regular font-kulim q-px-md q-py-sm"
                            label="Featured" />

                            <q-badge 
                            :color="car.badgeColor" 
                            class="absolute-top-right q-pa-sm z-index q-ma-md" 
                            rounded 
                            :label="car.year" />

                        <div class="absolute-bottom-right z-index row q-pa-md no-wrap q-gutter-sm">
                            <q-btn 
                              :class="car.btColor" 
                              round 
                              dense 
                              flat 
                              icon="favorite_border" 
                              />
                            <q-btn 
                              :class="car.btColor" 
                              round 
                              dense 
                              flat 
                              icon="compare_arrows" 
                              />
                        </div>

                        <q-img :src="car.image" class="border-radius-20" />
                        <q-badge
                          rounded
                          :color="car.badgeColor"
                          class="absolute text-subtitle2 q-px-md q-py-xs top-27 left-108 flex items-center"
                      >
                          <q-icon name="photo_library" size="14px" class="q-mr-xs" />
                          {{ car.pic }}
                      </q-badge>
                    </div>

                    <div class="q-pa-sm">
                        <div class="font-size-18 text-weight-regular font-mukta text-primary">{{ car.type }}</div>
                        <div class="text-h6 font-weight-600 font-mukta q-mb-sm">{{ car.name }}</div>
                        <div class="row q-pl-md-md q-pl-lg-none q-col-gutter-sm text-grey-7 q-mb-sm q-pl-sm">
                            <div class="col-6 text-subtitle2 text-weight-regular font-poppins flex items-center">
                                <q-icon name="calendar_month" size="18px" class="q-mr-xs" />
                                {{ car.model }}
                            </div>
                            <div class="col-6 text-subtitle2 text-weight-regular font-poppins flex items-center">
                                <q-icon name="speed" size="18px" class="q-mr-xs" />
                                {{ car.km }}
                            </div>
                            <div class="col-6 text-subtitle2 text-weight-regular font-poppins flex items-center">
                                <q-icon name="settings" size="18px" class="q-mr-xs" />
                                {{ car.transmission }}
                            </div>
                            <div class="col-6 flex items-center">
                                <q-icon name="local_gas_station" size="18px" class="q-mr-xs" />
                                {{ car.fuel }}
                            </div>
                            <div class="col-6 text-subtitle2 text-weight-regular font-poppins flex items-center">
                                <q-icon name="chair" size="18px" class="q-mr-xs" />
                                {{ car.seats }}
                            </div>
                            <div class="col-6 text-subtitle2 text-weight-regular font-poppins flex items-center">
                                <q-icon name="power" size="18px" class="q-mr-xs" />
                                {{ car.power }}
                            </div>
                        </div>

                        <q-separator class="q-my-lg" inset />
                        <div class="row q-pb-sm items-center justify-between">
                            <div class="text-primary text-weight-bold font-kulim text-h6">
                                AED {{ car.price.toLocaleString() }}
                            </div>
                            <q-btn 
                                class="bg-primary text-weight-regular font-size-18 font-kulim text-white q-px-lg border-radius-6" 
                                dense 
                                no-caps 
                                label="View Detail" 
                                />
                        </div>
                    </div>
                </q-card>
            </div>
        </div>

    </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { route } from 'quasar/wrappers'

const props = defineProps({
    initialCars: { type: Array, required: true },
    initialCategories: { type: Array, default: () => ['All Cars'] },
    initialSortOptions: {
        type: Array, default: () => [
            { label: 'Sort by (Default)', value: 'default' },
            { label: 'Price: Low to High', value: 'priceAsc' },
            { label: 'Price: High to Low', value: 'priceDesc' },
            { label: 'Year: Newest', value: 'yearDesc' },
            { label: 'Year: Oldest', value: 'yearAsc' }
        ]
    }
})

const activeCategory = ref('All Cars')
const sortBy = ref('default')

const cars = ref(props.initialCars)
const categories = props.initialCategories
const sortOptions = props.initialSortOptions

const filteredCars = computed(() => {
    let list = [...cars.value]

    if (activeCategory.value !== 'All Cars') {
        list = list.filter(c => c.type === activeCategory.value)
    }

    switch (sortBy.value) {
        case 'priceAsc': list.sort((a, b) => a.price - b.price); break;
        case 'priceDesc': list.sort((a, b) => b.price - a.price); break;
        case 'yearAsc': list.sort((a, b) => a.year - b.year); break;
        case 'yearDesc': list.sort((a, b) => b.year - a.year); break;
    }

    return list
})
</script>

<style scoped>
.z-index {
  z-index: 10;
}

.category-tabs {
  gap: 16px;
}
.cat-btn-wrapper {
    /* flex-shrink: 0; */
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: -10px;
}
.cat-underline {
  height: 3px;
  width: 100%;
  margin-top: 2px;
  border-radius: 3px;
}
</style>
