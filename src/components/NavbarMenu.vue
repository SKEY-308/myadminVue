<template>
  <nav>
    <!-- Navigation-drawer -->
    <v-navigation-drawer
      app
      permanent
      color="grey lighten-4"
      mini-variant
      mini-variant-width="90"
    >
      <v-avatar class="d-block text-center mx-auto mt-auto" size="50">
        <v-icon color="#2962FF" large>mdi-alpha</v-icon>
      </v-avatar>
      <p class="subtitle-2 mt-2 font-weight-bold text-center">Alpha</p>

      <v-divider class="mx-3 my-4"></v-divider>

      <v-list flat class="mt-5">
        <v-list-item-group v-model="selectedItem" color="#2962FF">
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            active-class="border"
            class=""
            :ripple="false"
            router
            :to="item.route"
          >
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
          </v-list-item>
        </v-list-item-group>
      </v-list>
      <!-- <div
        class="mx-auto"
        style="
          position: absolute;
          bottom: 20px;
          left: 0;
          right: 0;
          text-align: center;
        "
      >
        <v-btn icon :ripple="false">
          <v-badge color="red" dot overlap>
            <v-icon>mdi-bell-outline</v-icon>
          </v-badge> </v-btn
        ><br />
        <v-avatar size="30">
          <v-img
            src="https://raw.githubusercontent.com/iamshaunjp/vuetify-playlist/lesson-20/todo-ninja/public/avatar-4.png"
          ></v-img>
        </v-avatar>
      </div> -->
      <template v-slot:append>
        <div class="pa-6">
          <v-btn icon :ripple="false">
            <v-badge color="red" dot overlap>
              <v-icon>mdi-bell-outline</v-icon>
            </v-badge>
          </v-btn>
          <!-- <v-spacer></v-spacer> -->
          <v-avatar size="35">
            <v-img
              src="https://raw.githubusercontent.com/iamshaunjp/vuetify-playlist/lesson-20/todo-ninja/public/avatar-4.png"
            ></v-img>
          </v-avatar>
        </div>
      </template>
    </v-navigation-drawer>
    <!-- Navigation-drawer -->
  </nav>
</template>

<script>
export default {
  name: "NavbarMenu",
  components: {},
  data: () => ({
    selectedItem: 0,

    items: [
      { text: "Dashboard", icon: "mdi-expand-all", route: "/" },
      { text: "Dashboard", icon: "mdi-grid-large", route: "/p" },
      { text: "Dashboard", icon: "mdi-format-align-center", route: "/u" },
      { text: "Dashboard", icon: "mdi-cards-playing-outline", route: "/l" },
      { text: "Dashboard", icon: "mdi-chart-box-outline", route: "/j" },
    ],
  }),
};
</script>