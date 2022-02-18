<template>
  <div>
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
