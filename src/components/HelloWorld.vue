<template>
    <h1>{{ msg }}</h1>
    <p>
        Edit <code>components/HelloWorld.vue</code> to test hot module
        replacement.
    </p>
</template>

<script lang="ts">
    export default {
        name: "HelloWorld",
        props: {
            msg: String,
        },
    };
</script>
