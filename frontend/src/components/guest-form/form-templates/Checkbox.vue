<template>
  <v-checkbox
    v-model="checkbox"
    :label="`Agree with the rules : ${checkbox.toString()}`"
  ></v-checkbox>
</template>

<script>
export default {
  data: () => ({
    checkbox: false,
  }),
};
</script>