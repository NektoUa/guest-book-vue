<template>
  <div>
    <div v-for="answer in answers" :key="answer.nickname">
      <h3>
        {{ answer.nickname }}
      </h3>
      <span>{{ answer.star }} stars</span>
      <br />
      <span>{{ answer.date }}</span>
      <p>{{ answer.text }}</p>
    </div>
  </div>
</template>

<script>
import { eventEmitter } from "../../main";
export default {
  data() {
    return {
      answers: [],
    };
  },
  created() {
    eventEmitter.$on("yourAnswer", (opinionForm) => {
      this.answers.push(opinionForm);
    });
  },
};
</script>