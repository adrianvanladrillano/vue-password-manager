<template>
  <div>
    <v-row align="center" justify="center">
      <v-col cols="10">
        <div v-if="step == 1">
          <v-list-item two-line class="px-0">
            <v-list-item-content>
              <v-list-item-title class="font-weight-bold title">Create an account</v-list-item-title>
              <v-list-item-subtitle
                class="text-small text--secondary"
              >Choose what kind of account you want to create.</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <label class="text-small text--secondary">Fullname</label>
          <v-text-field
            class="custom-placeholder-color"
            solo
            background-color="grey lighten-4"
            flat
            placeholder="E.G. John Doe"
            dense
            v-model="fullname"
          ></v-text-field>

          <label class="text-small text--secondary">Email</label>
          <v-text-field
            class="custom-placeholder-color"
            solo
            background-color="grey lighten-4"
            flat
            placeholder="E.G. avpl.dev@example.com"
            dense
            v-model="email"
          ></v-text-field>

          <label class="text-small text--secondary">Password</label>
          <v-text-field
            class="custom-placeholder-color"
            solo
            background-color="grey lighten-4"
            flat
            placeholder="••••••"
            dense
            v-model="password"
          ></v-text-field>

          <label class="text-small text--secondary">Confirm Password</label>
          <v-text-field
            class="custom-placeholder-color"
            solo
            background-color="grey lighten-4"
            flat
            placeholder="••••••"
            dense
            v-model="cpassword"
          ></v-text-field>

          <v-btn @click="step++" block dark>Next</v-btn>
        </div>

        <div v-if="step == 2">
          <v-list-item two-line class="px-0 text-center">
            <v-list-item-content>
              <v-list-item-title class="font-weight-bold title">Set-up Passcode</v-list-item-title>
              <v-list-item-subtitle
                class="text-small text--secondary"
              >Choose what kind of account you want to create.</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <div class="d-flex">
            <v-text-field solo background-color="grey lighten-4" flat class="ma-2" v-model="input1"></v-text-field>
            <v-text-field
              solo
              background-color="grey lighten-4"
              flat
              class="ma-2"
              max="1"
              v-model="input2"
            ></v-text-field>
            <v-text-field solo background-color="grey lighten-4" flat class="ma-2" v-model="input3"></v-text-field>
            <v-text-field solo background-color="grey lighten-4" flat class="ma-2" v-model="input4"></v-text-field>
          </div>

          <div align="center" justify="center">
            <v-btn
              elevation="0"
              large
              fab
              class="ma-3"
              v-for="i in 9"
              :key="i"
              @click="handleInput(i)"
            >
              <h3>{{i}}</h3>
            </v-btn>
            <v-btn icon elevation="0" large fab class="ma-3" color="white"></v-btn>
            <v-btn elevation="0" large fab class="ma-3" @click="handleInput(0)">
              <h3>0</h3>
            </v-btn>
            <v-btn icon elevation="0" large fab class="ma-3" @click="handleBackspace()">
              <v-icon>mdi-backspace</v-icon>
            </v-btn>
          </div>
        </div>

        <div v-if="step == 3">
          <v-list-item two-line class="px-0 text-center">
            <v-list-item-content>
              <v-list-item-title class="font-weight-bold title">Review Account</v-list-item-title>
              <v-list-item-subtitle
                class="text-small text--secondary"
              >Choose what kind of account you want to create.</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <div>
            <v-list-item two-line>
              <v-list-item-avatar style="border: 1px solid #e1e1e1">
                <v-icon color="grey darken-4">mdi-account</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title class="font-weight-medium">{{fullname}}</v-list-item-title>
                <v-list-item-subtitle>Full name</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-list-item two-line>
              <v-list-item-avatar style="border: 1px solid #e1e1e1">
                <v-icon color="grey darken-4">mdi-email</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title class="font-weight-medium">{{email}}</v-list-item-title>
                <v-list-item-subtitle>Email Address</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-list-item two-line>
              <v-list-item-avatar style="border: 1px solid #e1e1e1">
                <v-icon color="grey darken-4">mdi-account-lock</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title class="font-weight-medium">{{password}}</v-list-item-title>
                <v-list-item-subtitle>Password</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-list-item two-line>
              <v-list-item-avatar style="border: 1px solid #e1e1e1">
                <v-icon color="grey darken-4">mdi-lock</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title
                  class="font-weight-medium"
                  style="letter-spacing: .3em"
                >{{`${input1}${input2}${input3}${input4}`}}</v-list-item-title>
                <v-list-item-subtitle>PIN</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>

            <v-btn block dark class="mt-5" @click="onSubmit()">Confirm Registration</v-btn>
          </div>
        </div>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      step: 1,
      input1: '',
      input2: '',
      input3: '',
      input4: '',

      fullname: '',
      email: '',
      password: '',
      cpassword: ''
    }
  },
  methods: {
    onSubmit() {
      axios
        .post('http://localhost:8000/api/auth/register', {
          name: this.fullname,
          email: this.email,
          password: this.password,
          pin: `${this.input1}${this.input2}${this.input3}${this.input4}`
        })
        .then(res => {
          console.log(res)
          alert('noice')
        })
        .catch(err => {
          console.error(err)
        })
    },
    handleInput(input) {
      if (this.input1 == '') {
        this.input1 = input
      } else if (this.input2 == '') {
        this.input2 = input
      } else if (this.input3 == '') {
        this.input3 = input
      } else if (this.input4 == '') {
        this.input4 = input
        this.step = 3
        alert('complete')
      }
    },
    handleBackspace(input) {
      if (this.input3 != '') {
        this.input3 = ''
      } else if (this.input2 != '') {
        this.input2 = ''
      } else if (this.input1 != '') {
        this.input1 = ''
      } else {
      }
    }
  }
}
</script>
<style>
.custom-placeholder-color {
  color: red !important;
  font-size: 0.8em;
}
.text-small {
  font-size: 0.7em;
}
</style>