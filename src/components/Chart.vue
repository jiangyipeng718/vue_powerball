<template>
    <h2 class="text-center font-semibold text-2xl">Number Distribution</h2>
    <div ref="plotlyRef" class="h-[85vh]"></div>
</template>

<script setup>

import Plotly from 'plotly.js-dist';
import { ref, onMounted } from 'vue';

const props = defineProps({
    data: Object
})

const coordinates = ref(props.data)


const plotlyRef = ref(null);

onMounted(
    () => {
        const TESTER = plotlyRef.value

        Plotly.newPlot(TESTER, [
            {
                y: coordinates.value.white.dates,
                x: coordinates.value.white.numbers,
                mode: 'markers',
                name: 'white',
                marker: { size: 9 }
            },
            {
                y: coordinates.value.red.dates,
                x: coordinates.value.red.numbers,
                mode: 'markers',
                type: 'scatter',
                name: 'power ball',
                marker: {
                    size: 12,
                    color: "red",
                }
            }

        ], {

            xaxis: { tickfont: { size: 20 } },
            yaxis: { tickfont: { size: 15 } },
        });



    }
)

</script>
