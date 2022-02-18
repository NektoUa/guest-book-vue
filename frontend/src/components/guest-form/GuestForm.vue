<template>
  <div>
    <h1>Please write your opinion</h1>

    <v-form v-model="valid">
      <v-col cols="12" md="6">
        <v-text-field
          v-model="person.nickname"
          :rules="nameRules"
          :counter="10"
          label="Nickname"
          required
        ></v-text-field>
        <Email />
        <br />
        <label for="person.text">Your opinion</label>
        <v-textarea
          :rules="opinionRules"
          required
          solo
          name="person.text"
          label="Write your opinion"
        ></v-textarea>
        <v-select :items="person.items" label="Star"></v-select>
        <v-checkbox
          v-model="checkbox"
          :label="`Agree with the rules : ${checkbox.toString()}`"
        ></v-checkbox>
        <v-btn color="secondary" elevation="2" @click="changeForm">Add</v-btn>
      </v-col>
    </v-form>
  </div>
</template>

<script>
import Email from "./form-templates/Email.vue";
import { eventEmitter } from "../../main";

export default {
  components: {
    Email,
  },
  data: () => ({
    person: {
      nickname: "",
      email: "",
      items: ["5", "4", "3", "2"],
      text: "",
    },
    valid: false,
    checkbox: true,
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 10 || "Name must be less than 10 characters",
    ],
    opinionRules: [(v) => !!v || "Field is empty"],
  }),

  methods: {
    changeForm() {
      if (this.checkbox) {
        eventEmitter.$emit("yourAnswer", this.person.nickname);
      }
    },
  },
};
</script>