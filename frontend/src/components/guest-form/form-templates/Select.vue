<template>
  <v-select :items="items" label="Star"></v-select>
</template>

<script>
export default {
  data: () => ({
    items: ["5", "4", "3", "2"],
  }),
};
</script>