<template>
  <v-card class="mt-8">
    <v-tabs v-model="timerType">
      <v-tab v-for="tab in tabsTitles" :key="tab">{{ tab }}</v-tab>
    </v-tabs>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      timerType: 0,
      tabsTitles: ["Pomodoro", "Short Break", "Long Break"],
    }
  },
}
</script>

<style language="sass" scoped>
.v-card {
  width: 600px;
}
</style>
