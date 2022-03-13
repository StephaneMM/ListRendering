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
