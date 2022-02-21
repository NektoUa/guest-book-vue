<template>
  <div>
    <h1>Please write your opinion</h1>
    <v-form v-model="valid">
      <v-col cols="12">
        <v-text-field
          v-model="person.nickname"
          :rules="nameRules"
          :counter="10"
          label="Nickname"
          required
        ></v-text-field>

        <v-text-field
          v-model="person.email"
          :rules="emailRules"
          label="E-mail"
          required
        ></v-text-field>
        <small id="emailHelp" class="form-text text-muted"
          >We'll never share your email with anyone else.</small
        >
        <br /><br />
        <label for="person.text">Your opinion</label>
        <v-textarea
          v-model="person.text"
          :rules="opinionRules"
          required
          solo
          name="person.text"
          label="Write your opinion"
        ></v-textarea>

        <v-select :items="items" label="Star"></v-select>
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
import { eventEmitter } from "../../main";

export default {
  data: () => ({
    person: {
      nickname: "",
      email: "",
      text: "",
      date: "",
    },
    valid: false,
    items: ["5", "4", "3", "2"],
    checkbox: false,
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 10 || "Name must be less than 10 characters",
    ],
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+/.test(v) || "E-mail must be valid",
    ],
    opinionRules: [(v) => !!v || "Field is empty"],
  }),
  computed: {
    rules() {
      let rule = [];
      let exception = "";
      this.person.nickname && this.person.nickname.length <= 10
        ? rule.push(true)
        : (exception = "Please write real nickname");
      this.person.email && this.person.email.match(/[a-z0-9]@\w+\.\w/gi)
        ? rule.push(true)
        : (exception = "E-mail must be valid and contain '@'");
      this.person.text
        ? rule.push(true)
        : (exception = "Please write your opinion");
      console.log(exception);
      return rule.length == 3 ? true : false;
    },
  },

  methods: {
    changeForm() {
      if (this.checkbox && this.rules) {
        this.person.date = new Date().toLocaleDateString();
        eventEmitter.$emit("yourAnswer", this.person);
        this.person = {
          nickname: "",
          email: "",
          text: "",
          date: "",
        };
      }
    },
  },
};
</script>