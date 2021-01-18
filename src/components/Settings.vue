<template>
    <v-dialog v-model="showSettings" persistent max-width="600px"> </v-dialog>
</template>
<script>
export default {
    props: {
        showSettings: {
            type: Boolean,
            required: true
        }
    }
};
</script>
