<template>
  <div id="app">
    <div class="contacts-list-settings">
      <SortButton @sortContacts="sortContacts" />

      <InputField @useSearch="useSearch" :search="search" />

      <ListButton @changeDisplayMode="changeDisplayMode" :listView="listView" />
    </div>

    <div v-if="!listView" class="contact-container contact-cards-container">
      <ContactCard
        v-for="contact in filteredContacts"
        :key="contact.id"
        :contact="contact"
      />
    </div>
    <div v-if="listView" class="contact-container contact-rows-container">
      <ContactRow
        v-for="contact in filteredContacts"
        :key="contact.id"
        :contact="contact"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SortButton from "./components/SortButton/";
import ListButton from "./components/ListButton/";
import InputField from "./components/InputField/";
import ContactCard from "./components/ContactCard/";
import ContactRow from "./components/ContactRow/";

export default {
  name: "App",

  data: () => ({
    contacts: [],
    listView: false,
    sorting: false,
    search: "",
  }),

  components: {
    ListButton,
    InputField,
    SortButton,
    ContactCard,
    ContactRow,
  },
  computed: {
    filteredContacts() {
      return this.contacts.filter((contact) => {
        return contact.fullName
          .toLowerCase()
          .normalize("NFD")
          .replace(/[\u0300-\u036f]/g, "")
          .match(this.search.toLowerCase());
      });
    },
  },
  methods: {
    sortContacts() {
      if (this.sorting) {
        return this.contacts.sort((a, b) => {
          this.sorting = !this.sorting;

          if (a.fullName > b.fullName) return -1;
          if (a.fullName < b.fullName) return 1;
          return 0;
        });
      } else {
        return this.contacts.sort((a, b) => {
          this.sorting = !this.sorting;

          if (a.fullName < b.fullName) return -1;
          if (a.fullName > b.fullName) return 1;
          return 0;
        });
      }
    },
    useSearch(search) {
      this.search = search;
    },
    changeDisplayMode() {
      this.listView = !this.listView;
    },
  },

  async created() {
    let simpleContactList = [];

    try {
      const response = await axios.get(`https://randomuser.me/api/?results=50`);
      const rawContacts = response.data.results;
      rawContacts.map((contact, i) =>
        simpleContactList.push({
          id: i,
          fullName: `${contact.name.first} ${contact.name.last}`,
          city: contact.location.city,
          email: contact.email,
          picture: contact.picture.large,
          phone: contact.phone,
        })
      );
      // console.log(simpleContactList);
      this.contacts = simpleContactList;
      // console.log(this.contacts);
    } catch (error) {
      console.log(error.response);
    }
  },
};
</script>

<style scope>
.contacts-list-settings {
  width: 100%;
  max-width: 840px;
  padding: 0px 45px;
  margin: 0 auto;

  display: flex;
  align-items: center;
  justify-content: space-between;
}

.contact-container {
  display: flex;
  width: 100%;
  max-width: 840px;
  padding: 0px 45px;
}

.contact-cards-container {
  /* box-sizing: border-box;
  justify-content: space-between; */
  flex-wrap: wrap;

  width: 100%;


  margin: 0 auto;

  gap: 50px 60px;
}

.contact-rows-container {
  flex-direction: column;
  gap: 18px;
}
</style>
