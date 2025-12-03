<template>
  <div class="row">
    <div
      v-for="(field, index) in fields"
      :key="index"
      :class="field.colClass ? field.colClass : 'col-12'"
    >
      <div class="q-pb-sm text-grey q-mb-xs text-subtitle">
        {{ field.label }} {{ field.required ? "*" : undefined }}
      </div>
      <div>
        <q-select
          v-if="field.fieldType === 'select'"
          emit-value
          outlined
          dense
          map-options
          v-model="modelValue[field.model]"
          :class="field.inputClass"
          :options="field.options"
          :rules="field.rules"
          behavior="menu"
          class="q-pb-lg text-weight-600 text-subtitle2 font-kulim border-radius-8"
          :menu-offset="[0, 10]"
          popup-content-class="select-organization text-weight-600 text-subtitle2 font-kulim text-grey border-radius-20"
        />
        <div v-else-if="field.fieldType === 'button'" class="text-center">
            <div class="q-mt-lg">
                <q-btn
                    :label="field.btnlabel"
                    :icon="field.icon"
                    no-caps
                    :color="field.color || 'primary'"
                    class="full-width q-py-sm text-white border-radius-8"
                    @click="field.onClick && field.onClick()"
                />
            </div>
        </div>
        <div v-else-if="field.fieldType === 'checkbox'" class="text-left">
          <q-checkbox
            v-model="modelValue[field.model]"
            label="Active Employee"
          />
        </div>
        <q-input
          v-else
          v-model="modelValue[field.model]"
          :type="field.type"
          :placeholder="field.placeholder"
          :prefix="field.prefix"
          :rules="field.rules"
          rounded
          outlined
          :class="field.inputClass"
          class="q-pb-lg"
        />
      </div>
    </div>
  </div>
</template>
<script setup>
defineOptions({
  name: "DynamicForm",
});
defineProps({
  fields: Array,
  modelValue: Object,
});
</script>
<style scoped></style>
