<template>
  <v-app id="inspire">
     <v-navigation-drawer 
     color=""
     v-model="drawer"
     app>
      <v-list-item >
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Vue Todo
          </v-list-item-title>
          <v-list-item-subtitle>
            best todo!
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
       app
      color="teal"
      dense
      dark
      prominent
    >
      <v-app-bar-nav-icon @click="drawer= !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>ALL TASK</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-checkbox-blank-badge-outline</v-icon>
      </v-btn>

      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            v-bind="attrs"
            v-on="on"
          >
            <v-icon>mdi-dots-horizontal-circle-outline</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            v-for="n in 3"
            :key="n"
            @click="() => {}"
          >
            <v-list-item-title>Task {{ n }}</v-list-item-title>
            
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
  
</template>

<script>
  export default {
    data: () => ({
       drawer: null,
        items: [
          { title: 'Todo', icon: 'mdi-checkbox-marked-circle-plus-outline',to: '/' },
          { title: 'About', icon: 'mdi-help-box',to: '/about' },
        ],
        }),
  }
</script>