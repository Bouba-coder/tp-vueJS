/* eslint-disable */
<script setup>
import { reactive, inject } from "vue";
const setValueChangeKey = Symbol("setValueChange");
defineProps({
  name: {
    type: String,
    required: true,
  },
  type: {
    type: String,
    required: false,
    default: "text",
  },
  as: {
    type: String,
    required: false,
  },
});

const values = reactive({});

inject(setValueChangeKey, (name, value) => {
  console.log("Set value change trigger", name, value);
  values[name] = value;
});
</script>

<template>
  <component :is="as" :type="type" :name="name" :value="value"
    ><slot></slot
  ></component>
</template>

<style scoped></style>
