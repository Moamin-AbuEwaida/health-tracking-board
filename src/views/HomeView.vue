<template>
  <v-app :style="{ background: $vuetify.theme.themes.light.background }">
    <v-layout row>
      <v-flex md8>
        <v-app
          :style="{ background: $vuetify.theme.themes.dark.background }"
          class="rounded-tr-xl rounded-br-xl"
        >
          <v-container>
            <v-row>
              <v-col cols="12" sm="12">
                <v-app-bar color="rgba(0,0,0,0)" flat class="mx-8 mb-8 mt-3">
                  <v-text-field
                    prepend-icon="mdi-magnify"
                    color="teal"
                    placeholder="Search your symptoms"
                    flat
                    success
                  ></v-text-field>
                  <v-spacer></v-spacer>
                  <v-chip class="ma-2" color="white">
                    <v-icon left color="teal">mdi-clock-time-nine</v-icon>
                    {{ dateTime }}
                  </v-chip>
                </v-app-bar>
              </v-col>
              <v-col cols="12" sm="12">
                <v-card class="mx-12 rounded-xl mt-n15">
                  <v-list-item three-line>
                    <v-list-item-content class="pa-10">
                      <v-list-item-title class="headline mb-1">
                        today
                        <span class="teal--text">-10%</span> discount<br />
                        on lung examinations
                      </v-list-item-title>
                      <v-list-item-subtitle>
                        The packge price includes: consultation<br />of a
                        pulmonologist, spirography
                        <spam class="teal--text">></spam>
                      </v-list-item-subtitle>
                    </v-list-item-content>
                    <v-list-item-avatar tile size="150" class="pr-10">
                      <v-img src="lungs.png"></v-img>
                    </v-list-item-avatar>
                  </v-list-item>
                </v-card>
              </v-col>
              <v-col cols="12" sm="12">
                <v-card class="mx-12 rounded-xl mt-n10">
                  <v-app-bar color="rgba(0,0,0,0)" flat class="ma-8">
                    <h5>Statistics of your health</h5>
                    <v-spacer></v-spacer>
                    <v-btn color="teal" text>
                      {{ year }}
                      <v-icon right>mdi-chevron-down</v-icon>
                    </v-btn>
                    <v-btn color="teal" rounded dark depressed>Year</v-btn>
                    <v-btn text>Month</v-btn>
                  </v-app-bar>
                  <template>
                    <v-sparkline
                      :value="value"
                      color="teal"
                      :smooth="radius || false"
                      :padding="padding"
                      :line-width="width"
                      :stroke-linecap="lineCap"
                      :fill="fill"
                      :type="type"
                      :auto-line-width="autoLineWidth"
                      auto-draw
                    ></v-sparkline>
                  </template>
                </v-card>
              </v-col>
              <v-col cols="12" sm="6">
                <v-card class="mx-12 rounded-xl mt-n4" color="teal" dark>
                  <v-list-item three-line>
                    <v-list-item-content class="pa-2">
                      <v-list-item-title class="headline mb-1">
                        Heart rate <br />
                        <h2>112 bpm</h2>
                      </v-list-item-title>
                    </v-list-item-content>
                    <v-list-item-avatar tile size="150" class="pr-10">
                      <v-icon size="100">fas fa-heartbeat</v-icon>
                    </v-list-item-avatar>
                  </v-list-item>
                </v-card>
              </v-col>
              <v-col cols="12" sm="6">
                <v-card class="mx-12 rounded-xl mt-n12">
                  <v-app-bar color="rgba(0,0,0,0)" flat class="ma-8">
                    <h5>Your activity</h5>
                    <v-spacer></v-spacer>
                    <v-btn color="teal" rounded dark depressed>Week</v-btn>
                    <v-btn text>Month</v-btn>
                  </v-app-bar>
                  <v-progress-circular
                    rotate="360"
                    size="90"
                    width="12"
                    value="50"
                    color="teal"
                    class="mt-n5 ml-5 mb-2"
                    >50</v-progress-circular
                  >
                  <v-progress-circular
                    rotate="360"
                    size="90"
                    width="12"
                    value="30"
                    color="red"
                    class="mt-n5 ml-2 mb-2"
                    >30</v-progress-circular
                  >
                  <v-progress-circular
                    rotate="360"
                    size="90"
                    width="12"
                    value="80"
                    color="blue"
                    class="mt-n5 ml-2 mb-2"
                    >80</v-progress-circular
                  >
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-app>
      </v-flex>
      <v-flex md4>
        <v-app :style="{ background: $vuetify.theme.themes.light.background }">
          <v-container></v-container>
        </v-app>
      </v-flex>
    </v-layout>
  </v-app>
</template>

<script>
const today = new Date();
const year = today.getFullYear();
const date =
  today.getFullYear() + "-" + (today.getMonth() + 1) + "-" + today.getDate();
const time =
  today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
const dateTime = date + " " + time;
export default {
  name: "HomeView",
  data: () => ({
    width: 2,
    radius: 10,
    padding: 8,
    lineCap: "round",
    value: [0, 2, 5, 9, 5, 10, 0, 0, 1, 8, 2, 9, 0],
    file: false,
    type: "trend",
    autoLineWidth: false,
    dateTime: dateTime,
    year: year,
  }),
  computed: {
    theme() {
      return this.$vuetify.theme.dark ? "dark" : "light";
    },
  },
};
</script>
