<template>
  <div>
    <span class="text--secondary text-small">Manage your</span>
    <h2 class="font-weight-medium">Passwords</h2>
    <v-row no-gutters>
      <v-col>
        <v-text-field
          dense
          solo
          background-color="grey lighten-4"
          flat
          label="Search"
          append-icon="mdi-magnify"
          hide-details
          class="my-5"
          v-model="search"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row no-gutters style="box-shadow: rgba(0, 0, 0, 0.1) 0px 1px 2px 0px;border-radius: 20px">
      <v-col cols="6" align="center" v-for="category in categories" :key="category" class="pa-1">
        <v-btn
          @click="toggleCategory(category)"
          block
          rounded
          depressed
          class="fill-height text-capitalize font-weight-regular"
          :class="active == category ? 'font-weight-bold white--text' : ''"
          :color="active == category ? 'grey darken-4' : 'white'"
          style="letter-spacing: 0em"
        >
          <v-icon left small>mdi-account</v-icon>
          {{category}}
        </v-btn>
      </v-col>
    </v-row>

    <div class="d-flex my-4">
      <v-chip
        v-if="search != ''"
        close
        label
        outlined
        class="text-capitalize mr-2"
        @click:close="search = ''"
      >{{search}}</v-chip>
      <v-chip
        v-if="active != 'all'"
        close
        label
        outlined
        class="text-capitalize"
        @click:close="active = 'all'"
      >{{active}}</v-chip>
    </div>

    <div class="d-flex my-4">
      <v-chip
        flat
        label
        color="white"
        class="text-capitalize text--secondary mr-2"
        @click:close="search = ''"
      >69 Total Items</v-chip>
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

    <v-dialog v-model="dialogView" fullscreen>
      <v-card>
        <DialogView />
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dialogView: false,
      search: '',
      active: 'all',
      categories: ['accounts', 'payment']
    }
  },
  methods: {
    onDialogView() {
      this.dialogView = true
    },
    toggleCategory(type) {
      this.active = type
    }
  }
}
</script>