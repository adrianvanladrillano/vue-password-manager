<template>
  <div>
    <v-bottom-navigation v-model="value" grow elevation="0" flat app color="black">
      <v-btn
        style="letter-spacing: 0em"
        class="font-weight-regular"
        :value="route.to"
        v-for="route in routes"
        :key="route.to"
        :to="route.to"
      >
        <span>{{route.name}}</span>
        <v-icon>{{route.icon}}</v-icon>
      </v-btn>
    </v-bottom-navigation>
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: null,
      routes: [
        { name: 'Accounts', icon: 'mdi-lock', to: '/dashboard' },
        { name: 'Settings', icon: 'mdi-tune', to: '/settings' }
      ]
    }
  }
}
</script>