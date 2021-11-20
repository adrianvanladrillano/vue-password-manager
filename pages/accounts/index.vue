<template>
  <div>
    <v-card class="pa-5">
      <h2 class="font-weight-medium">Hello, Adrian</h2>
      <p
        class="text--secondary text-small"
      >Lorem ipsum dolor sit amet consectetur, adipisicing elit. Amet, mollitia incidunt aut obcaecati aspernatur nostrum nobis a quae veritatis quos, cumque minus maxime blanditiis tenetur ipsum natus possimus ratione? Repudiandae?</p>
    </v-card>

    <v-text-field
      dense
      solo
      background-color="grey lighten-4"
      flat
      label="Search"
      append-icon="mdi-magnify"
      hide-details
      class="my-5"
    ></v-text-field>

    <v-row>
      <v-col cols="12" v-for="i in 2" :key="i">
        <v-card
          style="border-radius: 10px;box-shadow: rgba(0, 0, 0, 0.1) 0px 1px 2px 0px;"
          class="pa-2"
          color="primary"
          dark
        >
          <div class>
            <p class="px-0 py-0 my-0" style="font-size: 2em;">25</p>
            <p class="px-0 py-0 my-0">Secured shit</p>
          </div>
        </v-card>
      </v-col>
    </v-row>

    <div class="d-flex my-4">
      <v-menu v-model="menu" :close-on-content-click="false" :nudge-width="200" offset-x>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            v-bind="attrs"
            v-on="on"
            text
            class="text-capitalize font-weight-regular"
            style="letter-spacing: 0em;padding: 0"
          >
            Most Used
            <v-icon right>mdi-chevron-down</v-icon>
          </v-btn>
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
        <v-icon>mdi-format-list-bulleted</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-view-grid</v-icon>
      </v-btn>
    </div>

    <v-row>
      <v-col cols="12" xl="3" v-for="i in 10" :key="i">
        <Cards @showDialog="onDialogView" />
      </v-col>
    </v-row>

    <v-dialog v-model="dialogView">
      <DialogView />
    </v-dialog>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dialogView: false
    }
  },
  methods: {
    onDialogView() {
      this.dialogView = true
    }
  }
}
</script>