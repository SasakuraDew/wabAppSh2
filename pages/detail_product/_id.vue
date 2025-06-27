<template>
    <v-container>
        <v-card>
            <v-card-title>
                รายละเอียดสินค้า
            </v-card-title>
            <v-card-text>
                <div>
                    <strong>รหัสสินค้า:</strong> {{ productId }}
                </div>
            </v-card-text>
        </v-card>
    </v-container>
</template>

<script>
export default {
    async asyncData({ params }) {
        return {
            productId: params.id
        }
    }
}
</script>