<template>
  <div>
    <div>
      <v-list-item two-line class="px-0">
        <v-list-item-avatar color="black lighten-2" class="subheading white--text" size="50">
          <h3 class="font-weight-medium">{{step}}</h3>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title
            class="font-weight-bold title"
          >{{step == 1 ? 'Select Type' : 'Fill-up Details'}}</v-list-item-title>
          <v-list-item-subtitle
            class="text-small text--secondary"
          >Choose what kind of account you want to create.</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-row v-if="step == 1">
        <v-col cols="12">
          <v-card class="pa-3" outlined @click="chooseCategory('browser')">
            <v-row align="center" no-gutters>
              <v-col cols="3">
                <v-img
                  src="https://static.vecteezy.com/system/resources/previews/002/318/259/original/credit-card-icon-free-vector.jpg"
                ></v-img>
              </v-col>

              <v-col class="pa-2">
                <h3>Browser</h3>
                <p class="text-small">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
              </v-col>
            </v-row>
          </v-card>
        </v-col>

        <v-col cols="12">
          <v-card class="pa-3" outlined @click="chooseCategory('payment')">
            <v-row align="center" no-gutters>
              <v-col cols="3">
                <v-img
                  src="https://static.vecteezy.com/system/resources/previews/002/318/259/original/credit-card-icon-free-vector.jpg"
                ></v-img>
              </v-col>

              <v-col class="pa-2">
                <h3>Payment</h3>
                <p class="text-small">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </div>
    <div v-if="step==2">
      <div align="center">
        <v-avatar size="100" color style="border: 1px dashed #e1e1e1" @click="dialogImage = true">
          <v-icon x-large v-if="selected_icon == ''">mdi-image-outline</v-icon>
          <v-img v-else :src="selected_icon"></v-img>
        </v-avatar>
        <p class="text--secondary text-small mt-2">Change Icon</p>
      </div>
      <label class="text-small text--secondary">Title</label>
      <v-text-field
        class="custom-placeholder-color"
        solo
        background-color="grey lighten-4"
        flat
        placeholder="EG. Facebook, Grocery Card etc."
        dense
      ></v-text-field>
    </div>
    <div v-if="category == 'browser'" class="mt-2">
      <label class="text-small text--secondary">Account, username, e-mail or phone</label>
      <v-text-field
        class="custom-placeholder-color"
        solo
        background-color="grey lighten-4"
        flat
        placeholder="EG. avpl.dev@gmail.com"
        dense
      ></v-text-field>

      <label class="text-small text--secondary">Password</label>
      <v-text-field
        class="custom-placeholder-color"
        type="password"
        solo
        background-color="grey lighten-4"
        flat
        placeholder="••••••••"
        dense
      ></v-text-field>

      <label class="text-small text--secondary">Website URL</label>
      <v-text-field
        class="custom-placeholder-color"
        solo
        background-color="grey lighten-4"
        flat
        placeholder="https://www.facebook.com/"
        dense
      ></v-text-field>
    </div>

    <div v-if="category == 'payment'">
      <label class="text-small text--secondary">Account number</label>
      <v-text-field
        class="custom-placeholder-color"
        solo
        background-color="grey lighten-4"
        flat
        placeholder="E.G. 1234 5648 9012 3456"
        dense
      ></v-text-field>

      <label class="text-small text--secondary">Account holder</label>
      <v-text-field
        class="custom-placeholder-color"
        solo
        background-color="grey lighten-4"
        flat
        placeholder="E.G. Adrian Van Ladrillano"
        dense
      ></v-text-field>

      <v-row>
        <v-col cols="6">
          <label class="text-small text--secondary">PIN/CVV</label>
          <v-text-field
            type="password"
            class="custom-placeholder-color"
            solo
            background-color="grey lighten-4"
            flat
            placeholder="••••••"
            dense
          ></v-text-field>
        </v-col>

        <v-col cols="6">
          <label class="text-small text--secondary">Valid Thru</label>
          <v-text-field
            class="custom-placeholder-color"
            solo
            background-color="grey lighten-4"
            flat
            placeholder="E.G. 11/21"
            dense
          ></v-text-field>
        </v-col>
      </v-row>
    </div>

    <v-btn color="black" class="white--text text-capitalize" block v-if="step == 2">Confirm</v-btn>

    <v-dialog v-model="dialogImage">
      <v-card>
        <v-card-title>Choose Icon</v-card-title>
        <v-container>
          <v-combobox
            solo
            dense
            flat
            background-color="grey lighten-4"
            placeholder="Search Icon or paste link here.."
            :items="icons"
            item-text="logo"
            v-model="icon"
          >
            <template v-slot:item="data">
              <v-list-item-avatar>
                <img :src="data.item.logo" />
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title v-html="data.item.name"></v-list-item-title>
              </v-list-item-content>
            </template>
          </v-combobox>
        </v-container>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="black" class="white--text" @click="applyLogo()">Select</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
import base64js from 'base64-js'
export default {
  data() {
    return {
      step: 1,
      logo: '',
      parsed: '',
      dialogImage: false,
      category: '',
      icon: '',
      selected_icon: '',
      icons: [
        {
          name: 'Facebook',
          logo:
            'https://facebookbrand.com/wp-content/uploads/2019/04/f_logo_RGB-Hex-Blue_512.png?w=512&h=512'
        }
      ]
    }
  },
  methods: {
    applyLogo() {
      if (typeof this.icon === 'object') {
        this.selected_icon = this.icon.logo
      } else {
        this.selected_icon = this.icon
      }
      this.dialogImage = false
      this.icon = ''
    },
    chooseCategory(type) {
      this.category = type
      this.step = 2
    },
    imageToBase64(file) {
      var reader = new FileReader()
      reader.readAsDataURL(file)
      reader.onload = () => {
        console.log(reader.result)
        this.parsed = reader.result
      }
      reader.onerror = function(error) {
        console.log('Error: ', error)
      }
    }
  }
}
</script>
<style>
.text-small {
  font-size: 0.7em;
}
.custom-placeholder-color {
  color: red !important;
  font-size: 0.8em;
}
</style>