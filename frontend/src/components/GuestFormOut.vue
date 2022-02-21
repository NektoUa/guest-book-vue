<template>
  <div class="inline-flex justify-center mb-6" flat tile>
    <GuestForm />
    <FormOut />
  </div>
</template>

<script>
import GuestForm from "./guest-form/GuestForm.vue";
import FormOut from "./guest-form/FormOut.vue";

export default {
  components: {
    GuestForm,
    FormOut,
  },
};
</script>
