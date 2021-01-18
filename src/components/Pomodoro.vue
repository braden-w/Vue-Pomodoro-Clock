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
            <h1 class="time">{{ displayMinutes }}:{{ displaySeconds }}</h1>
            <div class="buttons">
              <v-btn color="primary" @click="start"
                ><v-icon left small>mdi-play-circle-outline</v-icon>Start</v-btn
              >
              <v-btn color="error" @click="stop">
                <v-icon left small>mdi-stop-circle-outline</v-icon>
                Stop</v-btn
              >
              <v-btn @click="reset">
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
      display: { minutes: "00", seconds: "00" },
      totalSeconds: 25 * 60,
      timerType: 0,
      tabsTitles: ["Pomodoro", "Short Break", "Long Break"],
    }
  },
  computed: {
    displayMinutes() {
      return Math.floor(this.totalSeconds / 60)
    },
    displaySeconds() {
      const seconds = this.totalSeconds % 60
      return this.formatTime(seconds)
    },
  },
  methods: {
    formatTime(time) {
      if (time < 10) {
        return "0" + time
      }
      return time.toString()
    },
    start() {
      this.timerInstance = setInterval(() => {
        this.totalSeconds -= 1
      }, 1000)
    },
    stop() {
      clearInterval(this.timerInstance)
    },
    reset() {
      this.stop()
      this.totalSeconds = 25 * 60
    },
  },
}
</script>

<style language="sass" scoped>
.v-card {
  width: 600px;
}
.v-btn {
  margin: 0 2px;
}
.time {
  font-size: 80px;
  font-weight: 400;
  align: center;
}
</style>
