<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipped flating temporary>
      <v-list dense>
        <v-row class="ma-2 mb-3">
          <v-icon class="mx-4 fab fa-adobe" large></v-icon>
          <v-toolbar-title class="align-center"></v-toolbar-title>
        </v-row>
        <v-list-item v-for="(item) in items" :key="item.icon" link>
          <v-list-item-action>
            <v-icon>{{item.icon}}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{item.text}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-icon @click="drawer=!drawer" class="mb-2"></v-icon>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer" />
      <v-icon class="mx-4 fab fa-adobe" large></v-icon>
      <v-toolbar-title class="align-center">
        <span class="title font-weight-thin" style="color:#6d6875">Ayşenur Yıldız</span>
      </v-toolbar-title>
      <v-spacer />
      <v-text-field
        class="mt-5"
        placeholder="Search"
        single-line
        append-icon="mdi-magnify"
        color="#b7b7a4"
      />
      <v-spacer />
      <v-btn class="ml-0" icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
      <v-btn class="ma-2" icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>

      <div>
        <v-menu v-model="menu" :close-on-content-click="false" :nudge-width="250" offset-x>
          <template v-slot:activator="{on}">
            <v-avatar size="40">
              <img v-on="on" src="https://api.adorable.io/avatars/285/abott@adorable.png" />
            </v-avatar>
          </template>

          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title>Ayşenur Yıldız</v-list-item-title>
                  <v-list-item-subtitle>Welcome</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider />
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-action>
                <v-list-item-title>Settings</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-divider />
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-switch v-model="theme" color="#b7b7a4"></v-switch>
                </v-list-item-action>
                <v-list-item-title>Dark Theme</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer />
              <v-btn color="primary" text @click="menu=false">Logout</v-btn>
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>

    <v-content>
      <v-container>
        <v-row class="mb-4">
          <v-col sm="6" md="4" lg="3" v-for="(item,index) in 200" :key="index">
            <v-card>
              <v-img
                height="200px"
                :src="`https://picsum.photos/500/300?image=${(index+1)}`"
                :lazy-src="`https://picsum.photos/10/6?image=${(index+1)}`"
              ></v-img>
              <v-list>
                <v-list-item>
                  <v-list-item-avatar></v-list-item-avatar>
                  <v-list-item-content>
                    <v-list-item-title>{{index+1}} . resim</v-list-item-title>
                    <v-btn class="ml-8 mb-0" color="primary" height="10px" text>Add to chart</v-btn>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    menu: false,
    theme: false,
    drawer: false,
    items: [
      { icon: "mdi-trending-up", text: "Trend Topic" },
      { icon: "mdi-history", text: "History" },
      { icon: "mdi-playlist-play", text: "Channels" },
      { icon: "mdi-trending-up", text: "Subscribe" }
    ]
  }),
  watch: {
    theme: function(next) {
      this.$vuetify.theme.dark = next;
    }
  }
};
</script>
