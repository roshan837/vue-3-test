<template>
    <div class="container">
        <div class="dem">
            <h6>Digital Experience Monitoring</h6>
            <div class="expbox">
                <div class="users">
                    <div class="sunburst">
                        <div>
                            <h2>{{ data.web.total + data.mobile.total }}</h2>
                            <p>Users</p>
                        </div>
                        <BigCircle />
                    </div>
                </div>
                <div class="mode">
                    <div class="modecontainer">
                        <div class="content">
                            <div class="box" style="backgroundColor:cyan"></div>
                            <div style="font-size: 0.7rem;font-weight: 700;">Web</div>
                        </div>
                        <h2>{{ data.web.total }}</h2>
                    </div>
                    <div class="modecontainer">
                        <div class="content">
                            <div class="box" style="backgroundColor:purple"></div>
                            <div style="font-size: 0.7rem;font-weight: 700;">Mobile</div>
                        </div>
                        <h2>{{ data.mobile.total }}</h2>
                    </div>
                </div>
                <div class="divisions">
                    <div class="circlecontainer">
                        <div class="web">
                            <div v-for="(ele, index) in data.web.array" :key="index">
                                <SmallCircle :data="ele" />
                            </div>
                        </div>
                        <div class="mobile">
                            <div v-for="(ele, index) in data.mobile.array" :key="index">
                                <SmallCircle :data="ele" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script setup>
import SmallCircle from '../components/SmallCircle.vue';
import BigCircle from './BigCircle.vue'

const data = {
    web: {
        type: "web",
        total: 750,
        array: [
            {
                name: "chrome",
                users: 300,
                errors: 25
            },
            {
                name: "explorer",
                users: 200,
                errors: 20
            },
            {
                name: "safari",
                users: 100,
                errors: 10
            },
            {
                name: "mozilla",
                users: 150,
                errors: 15
            }
        ]
    },
    mobile: {
        type: "web",
        total: 350,
        array: [
            {
                name: "apple",
                users: 100,
                errors: 10
            },
            {
                name: "android",
                users: 250,
                errors: 15
            }
        ]
    }
}
</script>

<style lang="scss" scoped>
.container {
    height: fit-content;
    padding: 10px;
    background-color: rgba(70, 131, 180, 0.212);

    .dem {
        height: 100%;
        width: 45%;
        background-color: white;
        border-radius: 10px;

        h6 {
            padding: 0.5rem 1rem;
        }
    }
}

.expbox {
    width: 100%;
    display: flex;
    justify-content: space-around;
    padding: 0 0 0.5rem 0;

    .users {
        width: 40%;
        display: flex;
        justify-content: center;
        align-items: center;

        .sunburst {
            display: flex;
            justify-content: center;
            align-items: center;

            div {
                position: absolute;

                p {
                    padding-inline: 1rem;
                    font-size: 0.6rem;
                }
            }
        }
    }

    .mode {
        width: 20%;
        border-left: 1px solid rgba(128, 128, 128, 0.5);
        border-right: 1px solid rgba(128, 128, 128, 0.5);

        .modecontainer {
            margin-bottom: 1rem;

            .content {
                display: flex;

                .box {
                    margin-inline: 0.4rem;
                    height: 10px;
                    width: 10px;
                }
            }

            h2 {
                padding-inline: 20px;
            }
        }
    }

    .divisions {
        width: 40%;

        .circlecontainer {

            .web,
            .mobile {
                display: flex;
                flex-wrap: wrap;
            }
        }
    }
}
</style>