<template>
  <div>
    <v-row>
      <v-col>
        <v-list-item two-line>
          <v-list-item-avatar width="56" height="56">
            <v-img
              style="width: 100%"
              src="https://images.squarespace-cdn.com/content/v1/5bf6023e9772aeb688f70ec0/1549845045984-IVOF0EE52RWX1DN587UO/blackpinkjennie+.jpg?format=500w"
            ></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title
              class="text-regular font-weight-medium grey--text text--darken-4"
            >Adrian Van Ladrillano</v-list-item-title>
            <v-list-item-subtitle class="text-regular">avpl.dev@gmail.com</v-list-item-subtitle>
          </v-list-item-content>
          <v-list-item-actions>
            <v-btn icon>
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </v-list-item-actions>
        </v-list-item>
      </v-col>
    </v-row>

    <v-text-field solo flat background-color="#F3F3F3" label="Search" append-icon="mdi-magnify"></v-text-field>

    <div class="d-flex">
      <v-menu v-model="menu" :close-on-content-click="false" :nudge-width="200" offset-x>
        <template v-slot:activator="{ on, attrs }">
          <v-btn text v-bind="attrs" v-on="on" class="text-capitalize">Active</v-btn>
        </template>

        <v-card>
          <v-list>
            <v-list-item>
              <v-list-item-avatar>
                <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title>John Leider</v-list-item-title>
                <v-list-item-subtitle>Founder of Vuetify</v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn :class="fav ? 'red--text' : ''" icon @click="fav = !fav">
                  <v-icon>mdi-heart</v-icon>
                </v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-list>

          <v-divider></v-divider>

          <v-list>
            <v-list-item>
              <v-list-item-action>
                <v-switch v-model="message" color="purple"></v-switch>
              </v-list-item-action>
              <v-list-item-title>Enable messages</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-action>
                <v-switch v-model="hints" color="purple"></v-switch>
              </v-list-item-action>
              <v-list-item-title>Enable hints</v-list-item-title>
            </v-list-item>
          </v-list>

          <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn text @click="menu = false">Cancel</v-btn>
            <v-btn color="primary" text @click="menu = false">Save</v-btn>
          </v-card-actions>
        </v-card>
      </v-menu>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </div>

    <v-row v-for="i in 10" :key="i" no-gutters>
      <v-col>
        <Cards />
      </v-col>
    </v-row>
  </div>
</template>