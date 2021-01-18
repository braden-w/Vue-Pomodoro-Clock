<template>
    <v-dialog v-model="showSettings" persistent max-width="600px">
        <v-card>
            <v-card-title><span class="headline">Settings</span></v-card-title>
            <v-card-text>
                <v-text-field
                    v-for="(timer, i) in timers"
                    :key="i"
                    :label="timers[i].name"
                    type="number"
                    v-model="timers[i].minutes"
                />
            </v-card-text>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="blue darken-1" text="" @click="closeSettings"
                    >Close</v-btn
                >
                <v-btn color="blue darken-1" text="" @click="save(timers)"
                    >Save</v-btn
                >
            </v-card-actions></v-card
        >
    </v-dialog>
</template>
<script>
export default {
    props: {
        showSettings: {
            type: Boolean,
            required: true
        },
        closeSettings: {
            type: Function,
            required: true
        },
        save: {
            type: Function,
            required: true
        },
        timers: {
            type: Array,
            require: true
        }
    }
};
</script>
