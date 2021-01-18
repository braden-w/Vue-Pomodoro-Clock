<template>
  <v-card>
    <vtabs v-model="timerType">
      <vtab v-for="tab in tabsTitles" :key="tab">{{ tab }}</vtab>
    </vtabs>
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
