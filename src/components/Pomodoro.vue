<template>
    <v-card class="mt-8">
        <v-tabs @change="changeCurrentTimer" v-model="currentTimer" grow>
            <v-tab v-for="timer in timers" :key="timer.name">
                {{ timer.name }}
            </v-tab>
            <v-tabs-items v-model="currentTimer">
                <v-tab-item> </v-tab-item>
            </v-tabs-items>
        </v-tabs>

        <v-card
            color="basil"
            flat
            class="pa-5 d-flex flex-column justify-center align-center"
        >
            <h1 class="time">{{ displayMinutes }}:{{ displaySeconds }}</h1>
            <div class="buttons">
                <v-btn color="primary" @click="start"
                    ><v-icon left small>mdi-play-circle-outline</v-icon
                    >Start</v-btn
                >
                <v-btn color="error" @click="stop">
                    <v-icon left small>mdi-stop-circle-outline</v-icon>
                    Stop</v-btn
                >
                <v-btn @click="reset" :disabled="isRunning">
                    <v-icon left small>mdi-restart</v-icon>
                    Reset</v-btn
                >
            </div>
        </v-card>
        <Settings
            :showSettings="showSettings"
            :closeSettings="closeSettings"
            :save="save"
            :timers="timers"
        ></Settings>
    </v-card>
</template>

<script>
import Settings from "./Settings.vue";
export default {
    components: {
        Settings
    },
    props: {
        showSettings: {
            type: Boolean,
            required: true
        },
        closeSettings: {
            type: Function,
            required: true
        }
    },
    data() {
        return {
            isRunning: false,
            display: { minutes: "00", seconds: "00" },
            totalSeconds: 25 * 60,
            currentTimer: 0,
            timers: [
                { name: "Pomodoro", minutes: 25 },
                { name: "Short Break", minutes: 5 },
                { name: "Long Break", minutes: 10 }
            ]
        };
    },
    computed: {
        displayMinutes() {
            return Math.floor(this.totalSeconds / 60);
        },
        displaySeconds() {
            const seconds = this.totalSeconds % 60;
            return this.formatTime(seconds);
        }
    },
    methods: {
        formatTime(time) {
            if (time < 10) {
                return "0" + time;
            }
            return time.toString();
        },
        start() {
            if (!this.isRunning) {
                this.timerInstance = setInterval(() => {
                    if (this.totalSeconds <= 0) {
                        this.stop();
                        return;
                    }
                    this.totalSeconds -= 1;
                }, 1000);
            }
            this.isRunning = true;
        },
        stop() {
            this.isRunning = false;
            clearInterval(this.timerInstance);
        },
        reset() {
            this.stop();
            this.totalSeconds = this.timers[this.currentTimer].minutes * 60;
        },
        changeCurrentTimer(num) {
            this.currentTimer = num;
            // TODO: Make this toggleable
            this.reset();
        },
        save(timerData) {
            this.timers = this.timers.map((timer, i) => {
                return { ...timer, minutes: parseInt(timerData[i].minutes) };
            });
            this.closeSettings();
        }
    }
};
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
