<template>
    <v-container>
        <v-row justify="center" align="center" style="height: 100vh;">
            <v-col cols="12" md="6" class="text-center">
                <v-card>
                    <v-card-title>
                        Hello World
                    </v-card-title>
                    <v-card-actions>
                        <v-btn color="primary" @click="$router.push('/inspire')">
                            inspire.vue
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: 'SignupPage'
}
</script>