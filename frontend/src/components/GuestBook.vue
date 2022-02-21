<template>
  <div class="spacing-playground px-14 mx-3" flat tile>
    <Navbar />
    <GuestFormOut />
    <Footer />
  </div>
</template>

<script>
import Navbar from "./templates/Navbar.vue";
import GuestFormOut from "./GuestFormOut.vue";
import Footer from "./templates/Footer.vue";

export default {
  components: {
    Navbar,
    GuestFormOut,
    Footer,
  },
};
</script>
