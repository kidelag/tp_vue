<script setup>
  import { inject } from "vue";
  import { data as dataKey } from "./DataProviderKeys";
  import { error as errorKey } from "./ErrorProviderKeys";

  const props = defineProps({
    name: {
      type: String,
      required: true,
    },
    as: {
      type: String,
      required: true,
      default: "input",
    },
  });

  const dataValue = inject(dataKey);
  const errorValue = inject(errorKey) || {};
  const currentError = errorValue[props.name];

  const value = dataValue[props.name];

  const handleChange = (event) => {
    dataValue[props.name] = event.target.value;
  };
</script>

<template>
  <component v-bind:is="as" :value="value" @input="handleChange"></component>
  <div v-show="currentError">{{ currentError }}</div>
</template>