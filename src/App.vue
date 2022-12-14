<script setup>
import Formik from "./components/Formik.vue";
const submit = (data) => {
  console.log("debug here", data);
};
</script>

<template>
  <main>
    <Formik @submitFinal="submit" :validate="() => {}" v-slot="{ handleSubmit }">
      <form @submit.prevent="handleSubmit">
      <button type="submit">submit</button>
    </form>
    </Formik>
  </main>
</template>
