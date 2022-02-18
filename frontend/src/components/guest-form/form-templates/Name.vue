<template>
  <v-text-field
    v-model="nickname"
    :rules="nameRules"
    :counter="10"
    label="Nickname"
    required
  ></v-text-field>
</template>

<script>
export default {
  data: () => ({
    nickname: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 10 || "Name must be less than 10 characters",
    ],
  }),
};
</script>