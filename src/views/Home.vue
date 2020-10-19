<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <div>
            <p>
                <span :style="{ marginRight: '10px' }"> 年龄：{{ age }} </span>
                <button @click="useAge">++</button>
            </p>
            <p>
                <span
                    ref="measurementsElement"
                    :style="{ marginRight: '10px' }"
                >
                    三围：{{ measurements }}
                </span>
                <button @click="useMeasurements">++</button>
            </p>
        </div>
        <HelloWorld msg="Hello Vue3.0 + Vite" />
    </div>
</template>

<script lang="ts">
    import HelloWorld from "../components/HelloWorld.vue";
    import { onMounted, reactive, ref } from "vue";

    export default {
        components: { HelloWorld },
        data: () => ({ a: 1 }),
        methods: {
            test() {
                console.log(this.a);
            },
        },
        mounted() {
            this.test();
        },
        setup() {
            const ageData = {
                age: ref(18),
                useAge() {
                    ageData.age.value++;
                },
            };

            const measurementsData = {
                measurements: reactive({ bust: 71, waist: 63, buttocks: 82 }) as {
                    [key: string]: number;
                },
                useMeasurements() {
                    Object.keys(measurementsData.measurements).forEach(
                        (key: string): void => {
                            measurementsData.measurements[key]++;
                        }
                    );
                },
            };

            const measurementsElement: { value: HTMLElement } = ref(document.body);
            onMounted(() => {
                console.log(measurementsElement.value.innerHTML);
            });

            return { ...ageData, ...measurementsData, measurementsElement };
        },
    };
</script>
