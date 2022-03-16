<template>
  <div id="app">
    <PageTitle class="title">Meet the Team </PageTitle>
    <InputField
      id="search-input-header"
      @useSearch="useSearch"
      :search="search"
    />
    <div class="contacts-list-settings">
      <div class="settings-right-side">
        <SortButton @sortContacts="sortContacts" />

        <InputField
          id="search-input-settings"
          @useSearch="useSearch"
          :search="search"
        />
      </div>

      <ListButton @changeDisplayMode="changeDisplayMode" :listView="listView" />
    </div>
    <main>
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
    </main>
  </div>
</template>

<script>
import axios from "axios";

import PageTitle from "./components/Text/PageTitle/";
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
    PageTitle,
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
      this.contacts = simpleContactList;
    } catch (error) {
      console.log(error.response);
    }
  },
};
</script>

<style scope>
@import "./styles/global.css";

.contacts-list-settings {
  width: 100%;
  max-width: 750px;
  margin: 0 auto;

  display: flex;
  align-items: center;
  justify-content: space-between;
}

.contact-container {
  display: flex;
  width: 100%;
  max-width: 810px;
}

.contact-cards-container {
  justify-content: space-around;
  flex-wrap: wrap;
  width: 100%;

  margin: 0 auto;
}

.contact-rows-container {
  flex-direction: column;
  align-items: center;

  gap: 18px 0;
  margin: 0 auto;
}

.settings-right-side {
  display: flex;
  align-items: center;
}

#search-input-header {
  display: none;
}

@media only screen and (max-width: 450px) {
  #search-input-settings {
    display: none;
  }

  #search-input-header {
    display: flex;
    align-self: center;
    /* max-width: 0; */
  }

  .contacts-list-settings {
    padding: 0 40px;
  }

  .contact-container {
    padding: 0 20px;
  }
}

@media only screen and (max-width: 830px) {
  .contacts-list-settings {
    padding: 0 40px;
  }
}
</style>
