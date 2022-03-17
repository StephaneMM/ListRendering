<template>
  <div class="card-container" :style="cssVars">
    <Body> {{ contact.fullName }} </Body>

    <AvatarPicture :image="contact.picture" :pxSize="100" />

    <div class="infos">
      <BodySmall class="city"> {{ contact.city }} </BodySmall>
      <ContactIcons :emailAdress="contact.email" :phoneNumber="contact.phone" />
    </div>
  </div>
</template>

<script>
import backgroundImage from "@/resources/cardsBackgroundPaths";

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

  computed: {
    selectedBackground() {
      return backgroundImage[this.contact.id % backgroundImage.length];
    },
    cssVars() {
      return {
        "--background-image": `url(${this.selectedBackground})`,
      };
    },
  },
  props: {
    contact: {},
  },
};
</script>

<style scoped>
.card-container {
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

  background-image: var(--background-image);
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
  width: 100%;
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

@media screen and (max-width: 450px) {
  .card-container {
    width: 8.4375em;
    height: 13.75em;

    min-width: 0;
    min-height: 0;

    padding-top: 2.0625em;
    padding-bottom: 0.90625em;

    margin: 0.8125em 0.9375em;
  }

  .city {
    margin-bottom: 8.75px;
  }
}
</style>
