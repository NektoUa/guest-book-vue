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

        <v-text-field
          v-model="email"
          :rules="emailRules"
          label="E-mail"
          required
        ></v-text-field>
        <small id="emailHelp" class="form-text text-muted"
          >We'll never share your email with anyone else.</small
        >

        <label for="person.text">Your opinion</label>
        <v-textarea
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
        <span> {{ person.name }}</span>
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
    },
    valid: false,
    items: ["5", "4", "3", "2"],
    checkbox: false,
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