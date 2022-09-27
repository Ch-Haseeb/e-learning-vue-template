 <template>
  <v-navigation-drawer  app>
    <div class="text-center">
      <v-avatar class="mt-4" color="grey darken-1" size="64">
        <v-img
          aspect-ratio="30"
          src="https://yt3.ggpht.com/esazPAO03T0f0vKdByJvkDy6MSwjyG5f-c_2S2CJapszQ3KPQyZarpoqvgv0Us0atUbILytj=s88-c-k-c0x00ffffff-no-rj"
        />
      </v-avatar>
      <!-- <h2 >Arkis</h2> -->
    </div>
    <v-divider></v-divider>

    <v-list nav dense>
      <div v-for="(link, i) in links" :key="i">
        <v-list-item
          v-if="!link.subLinks"
          :to="link.to"
          :active-class="color"
          avatar
          class="v-list-item"
        >
          <v-list-item-icon>
            <v-icon>{{ link.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-title v-text="link.text" />
        </v-list-item>

        <v-list-group
          v-else
          :key="link.text"
          no-action
          :prepend-icon="link.icon"
          :value="false"
        >
          <template v-slot:activator>
            <v-list-item-title>{{ link.text }}</v-list-item-title>
          </template>

          <v-list-item
            v-for="sublink in link.subLinks"
            :to="sublink.to"
            :key="sublink.text"
          >
            <v-list-item-icon>
              <v-icon>{{ sublink.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-title>{{ sublink.text }}</v-list-item-title>
          </v-list-item>
        </v-list-group>
      </div>
    </v-list>
  </v-navigation-drawer>
</template>
  
  <script>
export default {
  name: "SideBarView",
  props: ['drawer'],
  data: () => ({
    links: [
      {
        to: "/",
        icon: "mdi-view-dashboard",
        text: "Dashboard",
      },
      {
        to: "/articles",
        icon: "mdi-clipboard",
        text: "Articles",
      },
      {
        to: "/couching",
        icon: "mdi-briefcase-eye",
        text: "Couching",
      },
      {
        icon: "mdi-view-compact",
        text: "eLearning",
        subLinks: [
          {
            to: "/elearning/content",
            text: "eLearning Content",
          },
          {
            text: "Compliance",
          },
          {
            text: "Compliance Reporting",
          },
          {
            text: "eLearning Reporting",
          },
          {
            text: "Course List",
          },
          {
            text: "My Courses",
          },
        ],
      },
      {
        to: "/admin",
        icon: "mdi-account-cog",
        text: "Admin",
      },
    ],
  }),
};
</script>
  
  <style scoped>
.v-application--is-ltr
  .v-list--dense.v-list--nav
  .v-list-group--no-action
  > .v-list-group__items
  > .v-list-item {
  padding: 0 8px;
}
</style>