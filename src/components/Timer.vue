<script>
export default {
    data() {
        return {
            now: new Date(),
        };
    },

    mounted() {
        this.setTime();
        this.timer = setInterval(this.setTime, 1000);
    },

    computed: {
        hourDegress() {
            return ((this.now.getHours() / 12) * 360) + 90;
        },
        minDegress() {
            return ((this.now.getMinutes() / 60) * 360) + 90;
        },
        secDegress() {
            return ((this.now.getSeconds() / 60) * 360) + 90;
        },
    },
    
    methods: {
        setTime() {
            this.now = new Date();
        },
    },
};

</script>

<template>
    <h1></h1>
    <div class="clock">
        <div class="clock-face">
            <div class="hand hour-hand" :style="{transform: `rotate(${hourDegress}deg)`}"></div>
            <div class="hand min-hand" :style="{transform: `rotate(${minDegress}deg)`}"></div>
            <div class="hand second-hand" :style="{transform: `rotate(${secDegress}deg)`}"></div>
        </div>
    </div>
</template>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    margin: 0;
    font-size: 2rem;
    display: flex;
    flex: 1;
    min-height: 100vh;
    align-items: center;
}

.clock {
    width: 20rem;
    height: 20rem;
    border: 20px solid rgba(255, 255, 255, 0.786);
    border-radius: 50%;
    margin: 50px auto;
    position: relative;
    padding: 2rem;
    box-shadow:
        0 0 0 4px rgba(0, 0, 0, 0.1),
        inset 0 0 0 3px #EFEFEF,
        inset 0 0 10px black,
        0 0 10px rgba(0, 0, 0, 0.2);
}

.clock-face {
    position: relative;
    width: 100%;
    height: 100%;
    transform: translateY(-3px);
    /* account for the height of the clock hands */
}

.hand {
    height: 6px;
    position: absolute;
    top: 50%;
    right: 50%;
    transform-origin: 100%;
    transform: rotate(90deg);
    transition: all 0.05s;
    border-radius: 50px 0px 0px 50px;
}

.hour-hand {
    width: 40%;
    background: rgb(184, 61, 65);
}

.min-hand {
    width: 50%;
    background: rgba(184, 61, 65, 0.597);
}

.second-hand {
    background: rgb(255, 255, 255);
    width: 50%;
    height: 3px;
}
</style>