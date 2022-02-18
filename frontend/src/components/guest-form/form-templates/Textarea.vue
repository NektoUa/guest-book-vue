<template>
  <div>
    <label for="person.text">Your opinion</label>
    <v-textarea
      :rules="opinionRules"
      required
      solo
      name="person.text"
      label="Write your opinion"
      @keyup.enter="changeText"
    ></v-textarea>
  </div>
</template>

<script>
import { eventEmitter } from "../../../main";

export default {
  data: () => ({
    text: "",
    opinionRules: [(v) => !!v || "Field is empty"],
  }),
  methods: {
    changeText() {
      eventEmitter.$emit("yourText", this.text);
    },
  },
};
</script>