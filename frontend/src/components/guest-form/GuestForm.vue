<template>
  <div>
    <h1>Please write your opinion</h1>

    <v-form v-model="valid">
      <v-col cols="12" md="6">
        <v-text-field
          v-model="nickname"
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
        <br />
        <label for="message">Your opinion</label>
        <v-textarea
          :rules="opinionRules"
          required
          solo
          name="message"
          label="Write your opinion"
        ></v-textarea>
        <v-select :items="items" label="Star"></v-select>
        <v-checkbox
          v-model="checkbox"
          :label="`Agree with the rules : ${checkbox.toString()}`"
        ></v-checkbox>
        <v-btn color="secondary" elevation="2">Subimitti</v-btn>
      </v-col>
    </v-form>
  </div>
</template>

<script>
export default {
  data: () => ({
    valid: false,
    checkbox: true,
    items: ["5", "4", "3", "2"],
    nickname: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 10 || "Name must be less than 10 characters",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+/.test(v) || "E-mail must be valid",
    ],
    opinionRules: [(v) => !!v || "Field is empty"],
  }),
};
</script>