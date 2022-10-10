<template>
  <v-container>
    <!--  -->
    <v-row class="mb-3" justify="center">
      <v-toolbar-title class="font-weight-regular subtitle-1">
        <span> Alpha Overview </span>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn color="#2962FF" text small> last sprint </v-btn>
    </v-row>
    <!--  -->
    <v-item-group mandatory>
      <v-row justify="center">
        <v-col
          cols="12"
          xs="6"
          sm="4"
          md="2"
          v-for="work in works"
          :key="work.title"
        >
          <v-item v-slot="{ active, toggle }">
            <v-card
              :color="active ? '#2962FF' : 'white'"
              class="d-flex align-center rounded-xl"
              dark
              height="200"
              @click="toggle"
            >
              <v-row>
                <v-col cols="12">
                  <v-list-item class="mt-10" three-line>
                    <v-list-item-content>
                      <div class="mb-4">
                        <v-icon x-large :color="active ? 'white' : '#2962FF'">{{
                          work.avatar
                        }}</v-icon>
                      </div>
                      <v-list-item-subtitle
                        :class="active ? 'white--text' : 'black--text'"
                        >{{ work.title }}</v-list-item-subtitle
                      >
                      <v-list-item-title
                        class="headline mb-1"
                        :class="active ? 'white--text' : 'black--text'"
                      >
                        <strong>{{ work.estimation }}</strong>
                      </v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </v-col>
              </v-row>
            </v-card>
          </v-item>
        </v-col>
      </v-row>
    </v-item-group>
    <!--  -->
    <!--  -->
    <v-row class="my-4" justify="center">
      <v-toolbar-title class="font-weight-regular subtitle-1">
        <span>Sprint Stories </span>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn color="#2962FF" text small>See all </v-btn>
    </v-row>
    <!--  -->
    <!--  -->
    <v-row justify="center">
      <!-- v-chart -->
      <v-col cols="12" md="6">
        <!-- <v-card> -->
        <!-- <v-row> -->
        <!-- <v-col cols="12"> -->
        <v-chart class="chart" :option="option" />
        <!-- </v-col> -->
        <!-- </v-row> -->
        <!-- </v-card> -->
      </v-col>
      <!-- v-chart -->

      <v-spacer></v-spacer>

      <v-col cols="12" md="6">
        <v-card
          hover
          color="grey lighten-5"
          v-for="storie in stories"
          :key="storie.pid"
        >
          <v-row dense class="caption font-weight-regular" align="center">
            <v-col cols="12" xs="2" sm="2" md="2">
              <div class="ml-3 mt-1">{{ storie.pid }}</div>
            </v-col>
            <v-col cols="12" xs="3" sm="3" md="3">
              <div class="ml-2 mt-1">{{ storie.title }}</div>
            </v-col>
            <v-col cols="12" xs="3" sm="3" md="3">
              <div class="ml-2 mt-1">{{ storie.status }}</div>
            </v-col>
            <v-col cols="12" xs="2" sm="2" md="2">
              <div class="ml-4 mt-1">{{ storie.quantity }}</div>
            </v-col>
            <v-col cols="12" xs="2" sm="2" md="2">
              <v-btn class="ml-3" icon text color="#2962FF">
                <v-icon small>mdi-dots-horizontal</v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
    <!--  -->
    <!--  -->
    <!--  -->
    <v-row class="my-4" justify="center">
      <v-toolbar-title class="font-weight-regular subtitle-1">
        <span>Team members </span>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn color="#2962FF" text small>Add member</v-btn>
    </v-row>
    <!--  -->
    <!--  -->
    <!--  -->
    <v-card color="grey lighten-5" hover class="mt-2" outlined>
      <v-row justify="center" dense>
        <v-col
          cols="12"
          sm="3"
          v-for="item in items"
          :key="item.title"
          align-self="center"
        >
          <v-list color="grey lighten-5" dense nav shaped>
            <v-list-item>
              <v-badge
                bordered
                bottom
                :color="item.color"
                dot
                offset-x="30"
                offset-y="20"
              >
                <v-list-item-avatar>
                  <v-avatar size="35">
                    <v-img :src="item.icon" small></v-img>
                  </v-avatar>
                </v-list-item-avatar>
              </v-badge>
              <v-list-item-content>
                <v-list-item-title class="caption font-weight-regular">{{
                  item.title
                }}</v-list-item-title>

                <v-list-item-subtitle class="caption font-weight-regular">{{
                  item.subtitle
                }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
import { use } from "echarts/core";
import { CanvasRenderer } from "echarts/renderers";
import { PieChart } from "echarts/charts";
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent,
} from "echarts/components";
import VChart, { THEME_KEY } from "vue-echarts";

use([
  CanvasRenderer,
  PieChart,
  TitleComponent,
  TooltipComponent,
  LegendComponent,
]);

export default {
  name: "HomeView",
  data() {
    return {
      toggle_exclusive: 1,
      option: {
        title: {
          text: "Alpha Chart",
          left: "left",
        },
        tooltip: {
          trigger: "item",
          formatter: "{a} <br/>{b} : {c} ({d}%)",
        },

        series: [
          {
            name: "Traffic Sources",
            type: "pie",
            radius: "75%",
            center: ["45%", "50%"],
            data: [
              { value: 335, name: "Direct" },
              { value: 310, name: "Email" },
              { value: 234, name: "Ad Networks" },
              { value: 135, name: "Video Ads" },
              { value: 1548, name: "Search Engines" },
            ],
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                // shadowOffsetY: 0,
                // shadowColor: "rgba(0, 0, 0, 0)",
              },
            },
          },
        ],
      },
      items: [
        {
          title: "AAE Ideapro",
          subtitle: "32 Story point",
          color: "#49D9A0",
          icon: "https://raw.githubusercontent.com/iamshaunjp/vuetify-playlist/lesson-20/todo-ninja/public/avatar-3.png",
        },
        {
          title: "Johny",
          subtitle: "8 Story point",
          color: "grey lighten",
          icon: "https://raw.githubusercontent.com/iamshaunjp/vuetify-playlist/lesson-20/todo-ninja/public/avatar-1.png",
        },
        {
          title: "Mimi",
          subtitle: "40 Story point",
          color: "grey lighten",
          icon: "https://raw.githubusercontent.com/iamshaunjp/vuetify-playlist/lesson-20/todo-ninja/public/avatar-2.png",
        },
        {
          title: "Stela",
          subtitle: "20 Story point",
          color: "#49D9A0",
          icon: "https://raw.githubusercontent.com/iamshaunjp/vuetify-playlist/lesson-20/todo-ninja/public/avatar-5.png",
        },
      ],
      stories: [
        {
          pid: "P42",
          title: "Onboarding",
          status: "Delivred",
          quantity: "3",
        },
        {
          pid: "P32",
          title: "User Profil",
          status: "Approved",
          quantity: "8",
        },
        {
          pid: "P56",
          title: "Landing Page",
          status: "Delivred",
          quantity: "12",
        },
        {
          pid: "P36",
          title: "Setting",
          status: "Approved",
          quantity: "9",
        },
      ],
      works: [
        {
          title: "Team Velocity",
          estimation: "52",
          avatar: "mdi-chart-box-outline",
        },
        {
          title: "Team Menbers",
          estimation: "12",
          avatar: "mdi-account-outline",
        },
        {
          title: "Task Delivred",
          estimation: "83",
          avatar: "mdi-bag-suitcase-outline",
        },
        {
          title: "Our Services",
          estimation: "53",
          avatar: "mdi-magnify-expand",
        },
        {
          title: "Spikes Delivred",
          estimation: "23",
          avatar: "mdi-motorbike",
        },
        {
          title: "News Events",
          estimation: "15",
          avatar: "mdi-earth",
        },
      ],
    };
  },
  components: {
    VChart,
  },
  provide: {
    [THEME_KEY]: "blue accent-4",
  },
};
</script>
