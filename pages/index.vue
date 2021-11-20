<template>
  <div>
    <v-row align="center" justify="center" style="height:  vh">
      <v-col cols="10" class="text-center">
        <v-img
          src="https://media.istockphoto.com/vectors/lock-icon-vector-id936681148?k=6&m=936681148&s=612x612&w=0&h=ysWzOwC-v9jHI9vCnebtI-WuGRrdZ3zcwTkbXR5Cl5I="
        ></v-img>
        <h1 class="display-1">
          Trusted
          <br />and secure
        </h1>
        <p class="mt-5">
          You're passwords are protected
          <br />with high-level seurity.
        </p>

        <div class="d-flex flex-column">
          <v-btn color="black" dark router to="/register">Sign up</v-btn>
          <v-btn text class="mt-5" router to="/login">Login</v-btn>
        </div>
      </v-col>
    </v-row>
  </div>
</template>
<script>
export default {
  data() {
    return {}
  }
}
</script>