<template>
  <div class="card-container">
    <Body> {{ contact.fullName }} </Body>
    <AvatarPicture :image="contact.picture" />

    <div class="infos">
      <BodySmall class="city"> {{ contact.city }} </BodySmall>
      <ContactIcons :emailAdress="contact.email" :phoneNumber="contact.phone" />
    </div>
  </div>
</template>

<script>
import Body from "../Text/Body/";
import AvatarPicture from "../AvatarPicture/";
import BodySmall from "../Text/BodySmall/";
import ContactIcons from "../ContactIcons/";

export default {
  name: "ContactCard",

  data: () => ({}),

  components: {
    Body,
    AvatarPicture,
    BodySmall,
    ContactIcons,
  },

  props: {
    contact: {},
  },

  // computed: {
  // },
};
</script>

<style scoped>
.card-container {
  box-sizing: border-box;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;

  border-radius: 20px;

  width: 210px;
  height: 342px;

  padding-top: 65px;
  padding-bottom: 25px;

  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);

  background: url("/images/Card-background-Greenish.svg");
  background-position: center;
}

.infos {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.city {
  margin-bottom: 15px;
}
</style>
