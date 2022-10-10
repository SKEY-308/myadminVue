<template>
  <v-app>
    <!--  -->
    <!-- <appbar-menu /> -->

    <navbar-menu />
    <navbar-menu-right />
    <!--  -->
    <v-main class="grey lighten-2 mx-4">
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
// import AppbarMenu from "./components/AppbarMenu.vue";
import NavbarMenu from "./components/NavbarMenu.vue";
import NavbarMenuRight from "./components/NavbarMenuRight.vue";
export default {
  name: "App",
  components: {
    NavbarMenu,
    NavbarMenuRight,
    // AppbarMenu,
  },

  data: () => ({
    //
  }),
};
</script>
