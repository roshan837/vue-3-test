<script setup>
import { onMounted, ref } from 'vue';
import { Icon } from '@iconify/vue';
const icons = {
    chrome: "lucide:chrome",
    explorer: "bxl:internet-explorer",
    mozilla: "cib:mozilla-firefox",
    safari: "cib:safari",
    android: "akar-icons:android-fill",
    apple: "ant-design:apple-filled",
    unknown: "ant-design:file-unknown-filled"
};
const props = defineProps({
    size: {
        type: Number,
        default: 40
    },
    data: {
        value: Number,
        default: 0
    },
    icon: {
        value: String,
        default: "unknown"
    }
});
const outer = ref(null);
onMounted(() => {
    let x = (props.data.errors / props.data.users) * 100;
    outer.value.style.height = `${props.size}px`;
    outer.value.style.width = `${props.size}px`;
    outer.value.style.background = `conic-gradient(steelblue ${(100 - x) * 3.6}deg, orangered ${(100 - x) * 3.6}deg)`
});
</script>
<template>
    <el-tooltip placement="bottom" effect="light">
        <template #content>
            <div class="databox">
                <div class="box web"></div>
                <div>Users</div>
                <div>{{ data.users }}</div>
            </div>
            <div class="databox">
                <div class="box app"></div>
                <div>Errors</div>
                <div>{{ data.errors }}</div>
            </div>
        </template>
        <div class="outer" ref="outer">
            <div class="inner">
                <Icon :icon="icons[data.name]" color="steelblue" width="12" />
            </div>
        </div>
    </el-tooltip>
</template>
<style scoped lang="scss">
.outer {
    margin: 0 0 0.5rem 0.5rem;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;

    .inner {
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
        height: 80%;
        width: 80%;
        background-color: white;
    }
}

.databox {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.5rem;
    width: 3rem;
    height: 0.5rem;

    .box {
        height: 0.4rem;
        width: 0.4rem;
    }

    .web {
        background-color: aqua;
    }

    .app {
        background-color: orangered;
    }
}
</style>