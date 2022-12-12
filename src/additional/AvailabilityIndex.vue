<script lang="ts" setup>
import { Icon } from '@iconify/vue';
import { ref} from 'vue';
import PieChart from './PieChart.vue'

const percentage = ref(78);
const growth = ref(-3);
const color = growth.value < 0 ? ["orangered", "lightsteelblue"] : ["green", "lightsteelblue"];

</script>

<template>
    <div class="container">
        <h5>Availability Index
            <el-tooltip effect="light" content="This is Availability index" placement="right">
                <Icon icon="ant-design:info-circle-outlined" color="lightgray" />
            </el-tooltip>
        </h5>
        <main class="availabilitycontainer">
            <PieChart :data="percentage" :color="color" />
            <div class="availability">
                <h1>{{ percentage }}%</h1>
                <div class="index">
                    <h5 class="growth">{{ growth }}%
                        <Icon v-if="growth < 0" icon="emojione-monotone:red-triangle-pointed-down" color="orangered" />
                        <Icon v-else icon="emojione-monotone:red-triangle-pointed-up" color="green" />
                    </h5>
                </div>
            </div>
        </main>
    </div>
</template>

<style scoped lang="scss">
.container {
    width: 30%;
    margin: 2rem;
    border-radius: 10px;
    background-color: rgba(70, 131, 180, 0.200);
    padding: 0.5rem;

    .availabilitycontainer {
        display: flex;
        place-content: center;
        position: relative;

        .availability {
            position: absolute;
            bottom: 35%;

            .index {
                display: flex;
                place-content: center;

                .growth {
                    font-size: 0.7rem;
                }
            }

        }
    }
}
</style>