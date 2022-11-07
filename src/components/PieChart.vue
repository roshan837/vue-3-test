<template>
    <canvas id="pie"></canvas>
</template>
<script setup>
import * as echarts from 'echarts';
import { onMounted, ref } from 'vue';
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
    var myChart = echarts.init(document.getElementById('pie'));
    myChart.setOption({
        series: {
            type: 'pie',
            radius: ['75%', '90%'],
            color: props.color,
            itemStyle: {
                borderRadius: 5
            },
            label: {
                show: false
            },
            data: [props.data, 100 - props.data]
        }
    });
})
</script>