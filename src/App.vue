<template>
    <v-app>
        <v-main>
            <v-container>
                <v-row>
                    <v-col sm="6" offset-sm="3">
                        <Pomodoro />
                    </v-col>

                    <v-btn color="secondary" dark small absolute top right fab>
                        <v-icon>mdi-cog-outline</v-icon>
                    </v-btn>
                </v-row>
            </v-container>
        </v-main>
    </v-app>
</template>

<script>
import Pomodoro from "./components/Pomodoro.vue";

export default {
    name: "App",
    components: {
        Pomodoro
    }
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
