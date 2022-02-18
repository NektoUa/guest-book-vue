<template>
  <div>
    <v-text-field
      v-model.trim="email"
      :rules="emailRules"
      label="E-mail"
      required
      @mouseleave="changeEmail"
    ></v-text-field>
    <small id="emailHelp" class="form-text text-muted"
      >We'll never share your email with anyone else.</small
    >
  </div>
</template>

<script>
import { eventEmitter } from "../../../main";

export default {
  data: () => ({
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+/.test(v) || "E-mail must be valid",
    ],
  }),
  methods: {
    changeEmail() {
      eventEmitter.$emit("yourEmail", this.email);
    },
  },
};
</script>
