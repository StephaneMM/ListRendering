<template>
  <div class="card-container">
    <Body> {{ contact.fullName }} </Body>

    <AvatarPicture :image="contact.picture" :pxSize="100" />

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

  padding: 65px 5px 25px 5px;

  margin: 25px 30px;

  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);

  background: url("/images/Card-background-Greenish.svg");
  background-position: center;
  background-size: 104%;
}

.infos {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.city {
  margin-bottom: 15px;
}

@media screen and (max-width: 830px) {
  .card-container {
    width: 25.3vw;
    min-width: 9.75rem;

    height: 41.205vw;
    min-height: 13.125rem;

    padding-top: calc(0.5 * 7.8vw);
    padding-bottom: 4.2vw;

    margin: max(calc(0.5 * 3.6vw), 26px) calc(0.8 * 4.2vw);
  }

  .city {
    margin-bottom: 9px;
  }
}


</style>
