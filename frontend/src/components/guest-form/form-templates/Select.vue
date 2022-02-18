<template>
  <v-select :items="items" label="Star" @mouseleave="changeSelect"></v-select>
</template>

<script>
// import { eventEmitter } from "../../../main";

export default {
  data: () => ({
    items: ["5", "4", "3", "2"],
  }),
  //   methods: {
  //     changeSelect() {
  //       eventEmitter.$emit("yourSelect", this.items);
  //     },
  //   },
};
</script>