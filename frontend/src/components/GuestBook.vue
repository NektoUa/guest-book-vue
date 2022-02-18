<template>
  <div>
    <GuestFormOut />
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ullam temporibus
      similique sit cum eum corrupti officia, dolore quam repudiandae commodi.
      Accusamus voluptate incidunt vero tenetur sunt unde laborum dicta! Minima!
    </p>
    <form>
      <v-btn color="secondary" elevation="2">Add</v-btn>
    </form>
  </div>
</template>

<script>
import GuestFormOut from "./GuestFormOut.vue";

export default {
  components: {
    GuestFormOut,
  },
};
</script>
