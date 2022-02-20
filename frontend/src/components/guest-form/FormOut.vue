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
      answer: [],
    };
  },
  created() {
    eventEmitter.$on("yourAnswer", (opinionForm) => {
      // this.$set(this.answer, opinionForm.nickname, opinionForm);
      this.answer.push({ ggltol: 23, gfg: 45 });
      // this.answer = opinionForm;
      console.log(this.answer);
    });
  },
};
</script>