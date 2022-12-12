<template>
    <canvas id="pie" :style="{minHeight:'50px' ,minWidth:'50px'}"></canvas>
</template>
<script setup>
import * as echarts from 'echarts';
import { onMounted } from 'vue';
const props = defineProps({
    data: {
        type: Number,
        default: 100
    },
    color: {
        type: Array,
        default: ["green", "lightsteelblue"]
    }
})
onMounted(() => {
    console.log(props)
    const myChart = echarts.init(document.getElementById('pie'));
    myChart.setOption({
        series: {
            type: 'pie',
            radius: ['100%', '80%'],
            color: props.color,
            itemStyle: {
                borderRadius: 10
            },
            label: {
                show: false
            },
            data: [props.data, 100 - props.data]
        }
    });
})
</script>