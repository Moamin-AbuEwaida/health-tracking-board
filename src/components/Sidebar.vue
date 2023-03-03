<template>
  <nav>
    <v-navigation-drawer
      :v-model="drawer"
      dark
      app
      mini-variant
      mini-variant-width="100"
      class="teal"
    >
      <v-list>
        <v-list-item class="mb-12">
          <v-list-item-content>
            <v-icon class="mb-2" large>fas fa-hand-holding-medical</v-icon>
            <v-list-item-subtitle align="center">Medi</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-list flat>
        <v-list-item v-for="(item, i) in items" :key="i" router to="/">
          <v-list-item-content>
            <v-icon class="mb-2">{{ item.icon }}</v-icon>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-list style="position: absolute; bottom: 0" class="ml-3" flat>
        <v-list-item router to="/">
          <v-list-item-content>
            <v-icon right>fas fa-sign-out-alt</v-icon>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  name: "SideBar",
  data: () => ({
    drawer: true,
    items: [
      { icon: "fas fa-home" },
      { icon: "fas fa-user" },
      { icon: "fas fa-envelope" },
      { icon: "fas fa-cog" },
      { icon: "fas fa-question-circle" },
    ],
  }),
};
</script>

<style></style>
