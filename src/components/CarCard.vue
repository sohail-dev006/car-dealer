<template>
  <q-card class="car-card q-pa-sm bg-white border-radius-20">
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
      <div class="font-size-18 font-mukta text-primary">
        {{ car.type }}
      </div>

      <div class="text-h6 font-weight-600 font-mukta q-mb-sm">
        {{ car.name }}
      </div>

      <div class="row q-col-gutter-sm text-grey-7 q-mb-sm">
        <div class="col-6"><q-icon name="calendar_month" /> {{ car.model }}</div>
        <div class="col-6"><q-icon name="speed" /> {{ car.km }}</div>
        <div class="col-6"><q-icon name="settings" /> {{ car.transmission }}</div>
        <div class="col-6"><q-icon name="local_gas_station" /> {{ car.fuel }}</div>
        <div class="col-6"><q-icon name="chair" /> {{ car.seats }}</div>
        <div class="col-6"><q-icon name="power" /> {{ car.power }}</div>
      </div>

      <q-separator class="q-my-md" />

      <div class="row items-center justify-between">
        <div class="text-primary text-weight-bold text-h6">
          AED {{ car.price }}
        </div>
        <q-btn
          color="primary"
          no-caps
          label="View Detail"
          class="border-radius-6"
        />
      </div>
    </div>
  </q-card>
</template>

<script setup>
defineProps({
  car: Object
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
