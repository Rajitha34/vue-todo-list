<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6"> Vue Todo </v-list-item-title>
          <v-list-item-subtitle> best todo! </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="teal" dense dark>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>All Tasks</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-checkbox-blank-badge-outline</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-dots-horizontal-circle-outline</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
    </v-main>
    <v-footer v-bind="localAttrs" :padless="padless">
      <v-card flat tile width="100%" class="teal text-center">
        <v-card-text>
          <v-btn v-for="icon in icons" :key="icon" class="mx-16" icon>
            <v-icon size="24px" color="white">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-divider></v-divider>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    icons: ["mdi-check-circle", "mdi-calendar", "mdi-cog"],
    items: ["default", "absolute", "fixed"],
    padless: false,
    variant: "default",

    drawer: null,
    items: [
      {
        title: "Todo",
        icon: "mdi-checkbox-marked-circle-plus-outline",
        to: "/",
      },

      {
        title: "About",
        icon: "mdi-help-box",
        to: "/about",
      },
    ],
  }),
  computed: {
    localAttrs() {
      const attrs = {};

      if (this.variant === "default") {
        attrs.absolute = false;
        attrs.fixed = false;
      } else {
        attrs[this.variant] = true;
      }
      return attrs;
    },
  },
};
</script>
