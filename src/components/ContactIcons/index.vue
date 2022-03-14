<template>
  <div class="icons">
    <a :href="emailHref"> <Icon :icon="mailIcon" /> </a>
    <a :href="phoneHref"><Icon :icon="phoneIcon" /></a>
  </div>
</template>

<script>
import icons from "@/resources/iconsPaths";

import Icon from "../Icon";

export default {
  name: "ContactIcons",

  data: () => ({}),

  components: {
    Icon,
  },

  props: {
    emailAdress: { type: String, required: true },
    phoneNumber: { type: String, required: true },
  },

  computed: {
    mailIcon() {
      return icons.mail;
    },
    phoneIcon() {
      return icons.phone;
    },

    emailHref() {
      return `mailto:${this.emailAdress}`;
    },
    phoneHref() {
      return `tel:${this.phoneNumber}`;
    },
  },
};
</script>

<style scoped>
.icons {
  display: flex;

  margin: 0;
  padding: 0;
}
</style>
