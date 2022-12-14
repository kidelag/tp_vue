<script setup>
  import Formik from "./components/Formik.vue";
  import Field from "./components/Field.vue";

  const submit = (data) => {
    console.log("debug here", data);
  };

  const validate = (values) => {
    const errors = {};
    if (!values.email) {
      errors.email = "Required";
    } else if (!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i.test(values.email)) {
      errors.email = "Invalid email address";
    }
    return errors;
  };

  const initialValues = { email: "test@gmail.com", password: "" };
</script>

<template>
  <main>
    <Formik
        :initialValues="initialValues"
        @submitFinal="submit"
        :validate="validate"
        v-slot="{ handleSubmit }">
      <form @submit.prevent="handleSubmit">
        <Field :name="'email'" as="input" />
        <Field :name="'password'" />
        <button type="submit">envoyer</button>
      </form>
    </Formik>
  </main>
</template>