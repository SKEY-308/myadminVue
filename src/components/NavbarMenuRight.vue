<template>
  <nav class="d-sm-none d-sm-flex">
    <!--  -->
    <v-app-bar flat app color="grey lighten-2">
      <v-row>
        <!-- <v-toolbar-action flat color="grey lighten-2"> -->
        <v-btn icon text color="#2962FF">
          <v-icon text color="#2962FF">mdi-arrow-left-thin</v-icon>
        </v-btn>
        <v-btn icon text color="#2962FF">
          <v-icon text color="#2962FF" light>mdi-arrow-right-thin</v-icon>
        </v-btn>
        <!-- </v-toolbar-action> -->
        <v-spacer></v-spacer>

        <!-- <v-btn icon text color="#2962FF">
          <v-icon text color="#2962FF">mdi-radiobox-marked</v-icon>
        </v-btn> -->
      </v-row>
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        color="#2962FF"
        text
        class="d-none d-flex d-sm-none d-sm-flex d-md-flex"
      ></v-app-bar-nav-icon>
    </v-app-bar>
    <!--  -->
    <!-- Navigation-drawer Right -->
    <v-navigation-drawer
      v-model="drawer"
      app
      right
      color="grey lighten-4"
      width="270"
    >
      <v-toolbar flat color="grey lighten-4">
        <v-toolbar-title class="subtitle-1 font-weight-regular">
          Epics
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn small text color="#2962FF"> See all </v-btn>
      </v-toolbar>
      <!--  -->
      <v-list subheader two-line class="mt-n4">
        <v-list-item v-for="file in files" :key="file.title">
          <v-list-item-avatar>
            <v-icon dark :class="file.color" v-text="file.icon" small></v-icon>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title
              class="subtitle-2 font-weight-regular"
              v-text="file.title"
            ></v-list-item-title>
            <v-list-item-subtitle
              class="caption grey--text"
              v-text="file.subtitle"
            ></v-list-item-subtitle>
          </v-list-item-content>
          <v-list-item-action>
            <v-btn icon text color="#2962FF">
              <v-icon small>mdi-dots-vertical</v-icon>
            </v-btn>
          </v-list-item-action>
        </v-list-item>
      </v-list>
      <!--  -->
      <v-toolbar flat color="grey lighten-4" class="mt-n6">
        <v-toolbar-title class="subtitle-2 font-weight-regular mx-auto">
          Statistics
        </v-toolbar-title>
      </v-toolbar>
      <!-- vcard -->
      <v-card class="mx-2 pb-1" flat color="#EEEEEE">
        <v-row>
          <v-col cols="12" sm="5">
            <v-list-item two-line class="mt-n4">
              <v-list-item-content class="font-weight-regular mx-auto my-auto">
                <v-list-item-title class="subtitle-2 mt-2">
                  Project
                </v-list-item-title>
                <v-list-item-subtitle class="caption mt-3"
                  >progress</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-col cols="12" sm="4">
            <v-progress-circular
              :rotate="-90"
              :size="50"
              :width="3"
              :value="value1"
              color="#2962FF"
            >
              {{ value1 }}
            </v-progress-circular>
          </v-col>
          <v-col cols="12" sm="3" class="mt-3">
            <span class="font-weight-bold subtitle-1 ml-n8">%</span>
          </v-col>
        </v-row>
      </v-card>
      <!-- vcard -->
      <!-- vcard -->
      <v-card class="mx-2 pb-1" flat color="#EEEEEE">
        <v-row>
          <v-col cols="12" sm="5">
            <v-list-item two-line class="mt-n4">
              <v-list-item-content class="font-weight-regular mx-auto my-auto">
                <v-list-item-title class="subtitle-2 mt-2">
                  Business
                </v-list-item-title>
                <v-list-item-subtitle class="caption mt-3"
                  >goals</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-col cols="12" sm="4">
            <v-progress-circular
              :rotate="90"
              :size="50"
              :width="3"
              :value="value2"
              color="#D50000"
              class=""
            >
              {{ value2 }}
            </v-progress-circular>
          </v-col>
          <v-col cols="12" sm="3" class="mt-3">
            <span class="font-weight-bold subtitle-1 ml-n8">%</span>
          </v-col>
        </v-row>
      </v-card>
      <!-- vcard -->
      <!-- vcard -->
      <v-card class="mx-2 pb-1" flat color="#EEEEEE">
        <v-row>
          <v-col cols="12" sm="5">
            <v-list-item two-line class="mt-n4">
              <v-list-item-content class="font-weight-regular mx-auto my-auto">
                <v-list-item-title class="subtitle-2 mt-2">
                  Budget
                </v-list-item-title>
                <v-list-item-subtitle class="caption mt-3"
                  >used</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-col cols="12" sm="4">
            <v-progress-circular
              :rotate="-90"
              :size="50"
              :width="3"
              :value="value3"
              color="#2E7D32"
            >
              {{ value3 }}
            </v-progress-circular>
          </v-col>
          <v-col cols="12" sm="3" class="mt-3">
            <span class="font-weight-bold subtitle-1 ml-n8">%</span>
          </v-col>
        </v-row>
      </v-card>
      <!-- vcard -->
    </v-navigation-drawer>
    <!-- Navigation-drawer -->
  </nav>
</template>

<script>
export default {
  name: "NavbarMenu",
  components: {},
  data: () => ({
    drawer: true,
    interval: {},
    value1: 0,
    value2: 0,
    value3: 0,
    files: [
      {
        color: "green accent-4",
        icon: "mdi-tablet-cellphone",
        title: "Mobile Onboarding",
        subtitle: "Design",
      },
      {
        color: "red accent-4",
        icon: "mdi-card-account-details-outline",
        title: "Adding Item",
        subtitle: "Developpment",
      },
      {
        color: "orange accent-4",
        icon: "mdi-account-clock",
        title: "Admin Panel",
        subtitle: "Developpment",
      },
      {
        color: "purple accent-4",
        icon: "mdi-math-compass",
        title: "Mobile MVP",
        subtitle: "Design & Developpment",
      },
      {
        color: "blue accent-4",
        icon: "mdi-file-code-outline",
        title: "QR Scann",
        subtitle: "Research",
      },
    ],
  }),
  beforeDestroy() {
    clearInterval(this.interval);
  },
  mounted() {
    this.interval = setInterval(() => {
      if (this.value1 === 85) {
        return (this.value1 = 0);
      }
      this.value1 += 5;
    }, 2000);
    this.interval = setInterval(() => {
      if (this.value2 === 55) {
        return (this.value2 = 0);
      }
      this.value2 += 5;
    }, 2000);
    this.interval = setInterval(() => {
      if (this.value3 === 32) {
        return (this.value3 = 0);
      }
      this.value3 += 2;
    }, 2000);
  },
};
</script>