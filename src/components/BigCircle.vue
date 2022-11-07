<template>
    <canvas class="circular" id="main"></canvas>
</template>
<script setup>
import * as echarts from 'echarts';
import { onMounted, ref } from 'vue';
const data = ref([
    {
        name: 'Web',
        children: [
            {
                name: 'explorer',
                value: 200,
                children: [
                    {
                        name: 'Errors',
                        value: 20

                    },
                ]
            },
            {
                name: 'mozilla',
                value: 150,
                children: [
                    {
                        name: 'Errors',
                        value: 15
                    }
                ]
            },
            {
                name: 'chrome',
                value: 300,
                children: [
                    {

                        name: 'Errors',
                        value: 25

                    },
                ]
            },
            {
                name: 'safari',
                value: 150,
                children: [
                    {
                        name: 'Errors',
                        value: 10

                    },
                ]
            }
        ]
    },
    {
        name: 'Mobile',
        children: [
            {
                name: 'android',
                value: 250,
                children: [
                    {
                        name: 'Errors',
                        value: 15

                    },
                ]
            },
            {
                name: 'apple',
                value: 100,
                children: [
                    {
                        name: 'Errors',
                        value: 10

                    },
                ]
            }
        ]
    }
])
onMounted(() => {
    var myChart = echarts.init(document.getElementById('main'));
    myChart.setOption({
        series: {
            type: 'sunburst',
            data: data.value,
            radius: [40, '100%'],
            itemStyle: {
                borderRadius: 0,
                borderWidth: 0
            },
            label: {
                show: false,
            },
            color: ['#9a60b4', 'steelblue'],
        }
    });
})
</script>