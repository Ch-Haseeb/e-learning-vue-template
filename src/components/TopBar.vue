<template>
    <v-app-bar app elevate-on-scroll elevation="3"  color="white">
      <v-app-bar-nav-icon @click="$emit('drawerEvent')"></v-app-bar-nav-icon>
      <v-spacer />
      <v-spacer />
      <v-menu offset-y>
        <template v-slot:activator="{ attrs, on }">
          <span
            class="mx-5 mr-10"
            style="cursor: pointer"
            v-bind="attrs"
            v-on="on"
          >
           Help
          </span>
        </template>
      </v-menu>
      <v-menu offset-y>
        <template v-slot:activator="{ attrs, on }">
          <span style="cursor: pointer" v-bind="attrs" v-on="on">
            <v-chip link>
              <v-badge dot bottom color="green" offset-y="10" offset-x="10">
                <v-avatar size="40">
                  <v-img src="https://randomuser.me/api/portraits/women/81.jpg" />
                </v-avatar>
              </v-badge>
              <span class="ml-3">Jane Smith</span>
            </v-chip>
          </span>
        </template>
        <v-list width="250" class="py-0">
          <v-list-item two-line>
            <v-list-item-avatar>
              <img src="https://randomuser.me/api/portraits/women/81.jpg" />
            </v-list-item-avatar>
  
            <v-list-item-content>
              <v-list-item-title>Jane Smith</v-list-item-title>
              <v-list-item-subtitle>Logged In</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-divider />
          <v-list-item link v-for="(menu, i) in menus" :key="i">
            <v-list-item-icon>
              <v-icon>{{ menu.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-title>
              {{ menu.title }}
            </v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
  </template>
  
  <script>
  export default {
    name: "TopbarView",
    data() {
      return {
        menus: [
          { title: "Profile", icon: "mdi-account" },
          { title: "Change Password", icon: "mdi-key" },
          { title: "Setting", icon: "mdi-cog" },
          { title: "Logout", icon: "mdi-logout" },
        ],
      };
    },
  };
  </script>
  
  <style scoped></style>
  