<script>
import Clock from '@/components/Clock.vue';

export default {
    components: {
        Clock,
    },

    data() {
        return {
            regions: [
                { name: '英國', timeZone: 'Europe/London' },
                { name: '義大利', timeZone: 'Europe/Rome' },
                { name: '維也納', timeZone: 'Europe/Vienna' },
                { name: '土耳奇', timeZone: 'Europe/Istanbul' },
            ],
        };
    },

}
</script>

<template>
    <section class="container">
        <Clock v-for="(country, index) in regions" :key="index" :region="country.name" :timeZone="country.timeZone" />
    </section>
</template>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    font-family: 'clockicons';
    background-color: #000;
    color: #fff;
}
</style>