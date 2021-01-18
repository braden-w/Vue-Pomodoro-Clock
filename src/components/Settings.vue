<template>
    <v-dialog v-model="showSettings" persistent max-width="600px">
        <v-card>
            <v-card-title><span class="headline">Settings</span></v-card-title>
            <v-card-text>
                <v-text-field label="Pomodoro"></v-text-field>
            </v-card-text>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="blue darken-1" text="" @click="closeSettings"
                    >Close</v-btn
                >
                <v-btn color="blue darken-1" text="" @click="save">Save</v-btn>
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
        }
    }
};
</script>
