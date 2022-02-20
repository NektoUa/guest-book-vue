<template>
  <div>
    <h3>{{ answer.nickname }}</h3>
    <span>{{ answer.stars }}</span>
    <span>{{ answer.date }}</span>
    <p>{{ answer.text }}</p>
  </div>
</template>

<script>
import { eventEmitter } from "../../main";
export default {
  data() {
    return {
      answer: {},
    };
  },
  created() {
    eventEmitter.$on("yourAnswer", (opinionForm) => {
      this.answer = opinionForm;
    });
  },
};
</script>