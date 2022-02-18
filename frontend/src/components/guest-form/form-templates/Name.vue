<template>
  <v-text-field
    v-model.trim="nickname"
    :rules="nameRules"
    :counter="10"
    label="Nickname"
    required
    @mouseleave="changeName"
  ></v-text-field>
</template>

<script>
import { eventEmitter } from "../../../main";

export default {
  data: () => ({
    nickname: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 10 || "Name must be less than 10 characters",
    ],
  }),
  methods: {
    changeName() {
      eventEmitter.$emit("yourName", this.nickname);
    },
  },
};
</script>