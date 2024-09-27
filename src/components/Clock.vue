<script>
export default {
    props: {
        region: {
            type: String,
            default: '',
        },
        timeZone: {
            type: String,
            default: '',
        }
    },

    data() {
        return {
            currentDateTime: new Date(),
            timer: null,
        };
    },

    mounted() {
        this.updateTime();
        this.timer = setInterval(this.updateTime, 1000); 
    },

    unmounted() {
        clearInterval(this.timer);
    },

    computed: {
        formattedDate() {
            return this.currentDateTime.toLocaleDateString('zh-TW', {
                year: 'numeric',
                month: '2-digit',
                day: '2-digit',
            });
        },

        formattedTime() {
            return this.currentDateTime.toLocaleTimeString('zh-TW', {
                hour: '2-digit',
                minute: '2-digit',
                second: '2-digit',
                hour12: false,
            });
        },

    },

    methods: {
        updateTime() {
            this.currentDateTime = new Date(new Date().toLocaleString('en-US', { timeZone: this.timeZone }));
        },
    },
};

</script>

<template>
        <div class="timer">
            <h3>{{ region }}</h3>
            <time class="date">{{ formattedDate }}</time>
            <time class="clock">{{ formattedTime }}</time>
        </div>
</template>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.timer {
    display: flex;
    flex-direction: column;
    align-items: start;
    margin: 50px;
}

h3 {
    color: rgb(218, 204, 20);
}

.date {
    display: block;
    font-size: 24px;
}

.clock {
    font-size: 60px;
}
</style>