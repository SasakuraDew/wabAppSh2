<template>
    <div>
        <h1>Hello World</h1>
        <button @click="goHome" style="font-size: 20px; padding: 10px 20px;">Home</button>
    </div>
</template>

<script>
export default {
    methods: {
        goHome() {
            this.$router.push('/');
        }
    }
}
</script>