<template>
  <div>
    <label for="person.text">Your opinion</label>
    <v-textarea
      :rules="opinionRules"
      required
      solo
      name="person.text"
      label="Write your opinion"
    ></v-textarea>
  </div>
</template>

<script>
export default {
  data: () => ({
    text: "",
    opinionRules: [(v) => !!v || "Field is empty"],
  }),
};
</script>