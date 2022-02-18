<template>
  <div>
    <h1>Please write your opinion</h1>
    <v-form v-model="valid">
      <v-col cols="12" md="6">
        <Name />
        <Email />
        <Textarea />
        <v-select :items="items" label="Star"></v-select>
        <v-checkbox
          v-model="checkbox"
          :label="`Agree with the rules : ${checkbox.toString()}`"
        ></v-checkbox>
        <v-btn color="secondary" elevation="2">Add</v-btn>
        <span> {{ person.name }}</span>
      </v-col>
    </v-form>
  </div>
</template>

<script>
import Name from "./form-templates/Name.vue";
import Email from "./form-templates/Email.vue";
import Textarea from "./form-templates/Textarea.vue";
import { eventEmitter } from "../../main";

export default {
  components: {
    Name,
    Email,
    Textarea,
  },
  data: () => ({
    person: {
      nickname: "",
      email: "",
      text: "",
    },
    valid: false,
    items: ["5", "4", "3", "2"],
    checkbox: false,
    opinionRules: [(v) => !!v || "Field is empty"],
  }),
  created() {
    eventEmitter.$on("yourName", (name) => {
      this.person.nickname = name;
    });
    eventEmitter.$on("yourEmail", (email) => {
      this.person.email = email;
    });
    eventEmitter.$on("yourText", (text) => {
      this.person.text = text;
    });
  },

  //   methods: {
  //     changeForm() {
  //       if (this.checkbox) {
  //         eventEmitter.$emit("yourAnswer", this.person.nickname);
  //       }
  //     },
  //   },
};
</script>