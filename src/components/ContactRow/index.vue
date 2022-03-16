<template>
  <div class="card-container">
    <div class="contact-main">
      <AvatarPicture :image="contact.picture" />

      <div class="contact-infos">
        <Body> {{ contact.fullName }} </Body>
        <BodySmall> {{ contact.city }} </BodySmall>
      </div>
    </div>

    <ContactIcons
      class="contact-icons"
      :emailAdress="contact.email"
      :phoneNumber="contact.phone"
    />
    <div class="background-white"></div>
  </div>
</template>

<script>
import icons from "@/resources/iconsPaths";

import Body from "../Text/Body/";
import AvatarPicture from "../AvatarPicture/";
import BodySmall from "../Text/BodySmall/";
import ContactIcons from "../ContactIcons";

export default {
  name: "ContactRow",

  components: {
    Body,
    AvatarPicture,
    BodySmall,
    ContactIcons,
  },

  props: {
    contact: { require: true },
  },

  computed: {
    mailIcon() {
      return icons.mail;
    },
    phoneIcon() {
      return icons.phone;
    },
  },
};
</script>

<style scoped>
.card-container {
  display: flex;
  align-items: center;
  justify-content: space-between;

  border-radius: 20px;

  width: 100%;
  max-width: 750px;
  height: 100px;

  padding: 8px 30px;

  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);

  /* background-image: url("/images/Card-background-list-greenish.svg"); */
  /* background-position: center; */
  overflow: hidden;

  background-color: #a7b8a8;
}

.card-container * {
  z-index: 1;
}

.icons {
  display: flex;
}

.contact-infos {
  text-align: left;
  margin-left: 23px;
}

.contact-main {
  display: flex;
  align-items: center;
}

.background-white {
  position: absolute;
  left: clamp(73px, 20%, 50px);
  top: 0;
  height: 100%;
  width: 95%;
  border-top-left-radius: 42px;
  background-color: white;
  z-index: 0;
}

@media screen and (max-width: 450px) {
  .contact-icons {
    position: absolute;
    bottom: 10px;
    right: 15px;
  }
}
</style>
