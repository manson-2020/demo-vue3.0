<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <p>
            <button @click="countPlus">count: {{ count }} ++</button>
        </p>
        <HelloWorld msg="This is an About page" />
    </div>
</template>

<script lang="ts">
    import HelloWorld from "../components/HelloWorld.vue";

    export default {
        components: { HelloWorld },
        data: () => ({ count: 1 }),
        methods: {
            countPlus() {
                this.count++;
            },
        },
    };
</script>
