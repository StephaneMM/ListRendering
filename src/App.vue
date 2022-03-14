<template>
  <div id="app">
    <div class="contacts-list-settings">
      <SortButton @sortContacts="sortContacts" />

      <InputField @useSearch="useSearch" :search="search" />

      <ListButton @changeDisplayMode="changeDisplayMode" :listView="listView" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SortButton from "./components/SortButton/";
import ListButton from "./components/ListButton/";
import InputField from "./components/InputField/";


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


}

</style>
