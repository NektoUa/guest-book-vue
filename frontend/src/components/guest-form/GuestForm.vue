<template>
  <div>
    <h1>Please write your opinion</h1>
    <v-form v-model="valid">
      <v-col cols="12" md="6">
        <Name />
        <Email />
        <Textarea />
        <Select />
        <Checkbox />
        <v-btn color="secondary" elevation="2" @click="changeForm">Add</v-btn>
      </v-col>
    </v-form>
  </div>
</template>

<script>
import Name from "./form-templates/Name.vue";
import Email from "./form-templates/Email.vue";
import Textarea from "./form-templates/Textarea.vue";
import Select from "./form-templates/Select.vue";
import Checkbox from "./form-templates/Checkbox.vue";
import { eventEmitter } from "../../main";

export default {
  components: {
    Name,
    Email,
    Textarea,
    Select,
    Checkbox,
  },
  data: () => ({
    person: {
      nickname: "",
      email: "",
      items: ["5", "4", "3", "2"],
      text: "",
    },
    valid: false,
    checkbox: false,
    opinionRules: [(v) => !!v || "Field is empty"],
  }),

  //   methods: {
  //     changeForm() {
  //       if (this.checkbox) {
  //         eventEmitter.$emit("yourAnswer", this.person.nickname);
  //       }
  //     },
  //   },
};
</script>