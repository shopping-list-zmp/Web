<template>
  <nav-bar>
    <div>
      <div v-if="userAuth">
        <create-list></create-list>
        <show-lists></show-lists>
      </div>

      <div v-else>
        <guest-component></guest-component>
      </div>
    </div>
  </nav-bar>
</template>

<script>
import NavBar from "../../components/sideBar/SideBar";
import CreateList from "../../components/editList/CreateList.vue";
import showLists from "../../components/showList/showLists.vue";
import GuestComponent from "../../components/Home/GuestComponent.vue";

export default {
  components: { NavBar, CreateList, showLists, GuestComponent },
  computed: {
    userAuth() {
      return this.$store.getters.login;
    },
  }
};
</script>