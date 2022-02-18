<template>
  <div>
    <!-- <h3>{{ nickname }}</h3> -->
    <p>{{ answer }}</p>
  </div>
</template>

<script>
import { eventEmitter } from "../../main";
export default {
  data() {
    return {
      answer: "Medelin",
    };
  },
  created() {
    eventEmitter.$on("yourAnswer", (opinionForm) => {
      this.answer = opinionForm;
    });
  },
};
</script>