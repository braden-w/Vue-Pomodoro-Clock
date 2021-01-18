<template>
  <v-card class="mt-8">
    <v-tabs v-model="timerType" grow>
      <v-tab v-for="tab in tabsTitles" :key="tab">
        {{ tab }}
      </v-tab>
      <v-tabs-items v-model="timerType">
        <v-tab-item>
          <v-card
            color="basil"
            flat
            class="pa-5 d-flex flex-column justify-center align-center"
          >
            <h1 class="time">00:00</h1>
            <div class="buttons">
              <v-btn color="primary"
                ><v-icon left small>mdi-play-circle-outline</v-icon>Start</v-btn
              >
              <v-btn color="error">
                <v-icon left small>mdi-stop-circle-outline</v-icon>
                Stop</v-btn
              >
              <v-btn>
                <v-icon left small>mdi-restart</v-icon>
                Reset</v-btn
              >
            </div>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
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
.time {
  font-size: 80px;
  font-weight: 400;
  align: center;
}
</style>
