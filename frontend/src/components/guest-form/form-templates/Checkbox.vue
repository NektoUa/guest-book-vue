<template>
  <v-checkbox
    v-model="checkbox"
    :label="`Agree with the rules : ${checkbox.toString()}`"
  ></v-checkbox>
</template>

<script>
// import { eventEmitter } from "../../../main";

export default {
  data: () => ({
    checkbox: false,
  }),
};
</script>